# **最新版本是基于layui v2.2.3, 附件中有layui v1.0.7** 
demo地址：
https://shaojiepeng.github.io/layui-treetable/demo.html

https://shaojiepeng.github.io/layui-treetable/demo2.html

https://shaojiepeng.github.io/layui-treetable/demo3.html

### 2018.2.11 Updated
新增了复选框功能
- 使用方式：1. 实例化form 2. 传入checkbox参数 3. form.render()渲染页面
- 获取选中的row: layui.getSelected('id');
![输入图片说明](https://gitee.com/uploads/images/2018/0211/130206_ec642979_980808.png "1.png")
![输入图片说明](https://gitee.com/uploads/images/2018/0211/130310_bc3c9c4f_980808.png "2.png")

### 2018.2.1 Updated
新增树形菜单全部收起和全部展开功能，调用方式如下：
![输入图片说明](https://gitee.com/uploads/images/2018/0201/164613_9a74b476_980808.png "微信图片_20180201164558.png")

### 2017.12.11 Updated
- 添加expredable参数: 设置展示treetable时是否展开，默认为false; 请参考demo.html
- treetable显示多列的方式，参考以下，field的值要跟数据格式中的一致
```
var layout = [
        {name: '菜单名称', treeNodes: true, headerClass: 'value_col', colClass: 'value_col', style: 'width: 40%'},
        {name: 'Url', field: 'url', headerClass: 'value_col', colClass: 'value_col', style: 'width: 30%'},
        {name: '操作', headerClass: 'value_col', colClass: 'value_col', style: 'width: 30%', render: function(row) { return render(row)}}
    ];
```



#layui-treeGird

首先介绍一下[layui](https://www.layui.com/)，是一个模块化前端UI框架，遵循原生HTML/CSS/JS的书写与组织形式，门槛极低，拿来即用。

由于最近的项目中引进了layui，使用了树形菜单的内置模块，可是该功能并未完全满足需求。
layui是开源包，为满足需求，故基于layui-tree写了一个treetable.


#使用
1. 页面元素
```
<div id="demo"></div>
```
2. js代码
```
var layout = [
        {name: '菜单名称', treeNodes: true, headerClass: 'value_col', colClass: 'value_col', style: 'width: 60%'}
];
```

```
layui.use(['tree', 'layer', 'form'], function(){
              var layer = layui.layer, $ = layui.jquery;
              var form = layui.form();
          
              layui.treeGird({
                elem: '#demo',   //传入元素选择器
                nodes: [
                          {
                              "id": "1",
                              "name": "父节点1",
                              "children": [
                                  {
                                      "id": "11",
                                      "name": "子节点11"
                                  },
                                  {
                                      "id": "12",
                                      "name": "子节点12"
                                  }
                              ]
                          },
                          {
                              "id": "2",
                              "name": "父节点2",
                              "children": [
                                  {
                                      "id": "21",
                                      "name": "子节点21",
                                      "children": [
                                          {
                                              "id": "211",
                                              "name": "子节点211"
                                          }
                                      ]
                                  }
                              ]
                          }
                ],
                layout:layout
            });
        });
```


3.页面展示

![输入图片说明](https://git.oschina.net/uploads/images/2017/0523/144746_e6c438e1_980808.png "在这里输入图片标题")


#方法
语法：layui.treeGird(options)

options是一个对象参数，可支持的key如下表
![输入图片说明](https://git.oschina.net/uploads/images/2017/0523/150434_c4a6586b_980808.png "在这里输入图片标题")


#节点数据格式nodes
![nodes](https://git.oschina.net/uploads/images/2017/0523/151002_4ea8f20a_980808.png "在这里输入图片标题")


#列表头元素layout
![layout](https://git.oschina.net/uploads/images/2017/0523/151627_46e0ad19_980808.png "在这里输入图片标题")

自定义的render
```
var layout = [
        {name: '菜单名称', treeNodes: true, headerClass: 'value_col', colClass: 'value_col', style: 'width: 60%'},
        {name: '操作', headerClass: 'value_col', colClass: 'value_col', style: 'width: 20%', render: function(row) {
            return '<a class="layui-btn layui-btn-danger layui-btn-mini" onclick="del('+row.id+')"><i class="layui-icon">&#xe640;</i> 删除</a>';   //列渲染
        }},
];
```

效果如下：
![输入图片说明](https://git.oschina.net/uploads/images/2017/0523/151846_9790e8b3_980808.png "在这里输入图片标题")


#总结
灵感来源layui，感谢layui的开源。

