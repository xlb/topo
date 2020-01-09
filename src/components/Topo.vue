<template>
  
    <div id="relation-box">
  

	
		<input type='radio'  :value='0' v-model='sortFuntion'/>
		<label >dagre布局</label>
		
		<input type='radio'  :value='1' v-model='sortFuntion'/>
		<label >力导向布局</label><br>


    <template>
    <div 
    class="node"
    style="background: #88d6fb;"   v-for="item in nodeList"    :key="item.id"
     :id="'node-'+ item.id"
        :style="{left: item.left,
        top: item.top,
        width:nodeWidth,
        height:nodeHeight}"
    >
	<div style="  padding-top: 10px;
	text-align: center;">{{item.name}}</div>
	<div style="left: 10%;right: 10%;bottom: 10%;top: 20%;background: #ffffff;position: absolute;">
		<div >{{item.name}}</div>
		<div >{{item.name}}</div>
		<div >{{item.name}}</div>
		<div >{{item.name}}</div>
	</div>
</div>
    </template>

    </div>
 
</template>

<script>
import { jsPlumb } from "jsplumb";
import dagreD3 from 'dagre-d3'
import {ForceDirected} from "../util/ForceDirectedUtils"

export default {
    name: 'HelloWorld',
    props: {
        msg: String
    },

    data() {
        return {
            timer:null,
            sortFuntion:1,//0 g3,1自定义
            root : {

                nodes: [
                    {
                        id: '1',
                        name: '北京x',
                        type: 'address'
                    },
                    {
                        id: '2',
                        name: '苹果vc',
                        type: 'fruit'
                    },
                    {
                        id: '3',
                        name: '深圳fasd',
                        type: 'address'
                    },
                    {
                        id: '4',
                        name: '香蕉222',
                        type: 'fruit'
                    },
                    {
                        id: '5',
                        name: '上海xx',
                        type: 'address'
                    },
                    {
                        id: '6',
                        name: '111红茶',
                        type: 'fruit'
                    },
                    {
                        id: '7',
                        name: '北京xx',
                        type: 'address'
                    },
                    {
                        id: '8',
                        name: 'c果',
                        type: 'fruit'
                    },
                    {
                        id: '9',
                        name: '22深圳',
                        type: 'address'
                    },
                    {
                        id: '10',
                        name: '11香蕉',
                        type: 'fruit'
                    },
                    {
                        id: '11',
                        name: '上t',
                        type: 'address'
                    },
                    {
                        id: '12',
                        name: '红222茶',
                        type: 'fruit'
                    }
                    ,
                    {
                        id: '13',
                        name: '北京2xx',
                        type: 'address'
                    },
                    {
                        id: '14',
                        name: '11苹果',
                        type: 'fruit'
                    },
                    {
                        id: '15',
                        name: '深圳bb',
                        type: 'address'
                    },
                    {
                        id: '16',
                        name: 'dd香蕉',
                        type: 'fruit'
                    },
                    {
                        id: '17',
                        name: '上dd海',
                        type: 'address'
                    },
                    {
                        id: '18',
                        name: '红aa茶',
                        type: 'fruit'
                    },
                    {
                        id: '19',
                        name: '北京xx',
                        type: 'address'
                    },
                    {
                        id: '20',
                        name: '苹s果',
                        type: 'fruit'
                    },
                    {
                        id: '21',
                        name: '深f圳',
                        type: 'address'
                    },
                    {
                        id: '22',
                        name: '香s蕉',
                        type: 'fruit'
                    },
                    {
                        id: '23',
                        name: '上海sd',
                        type: 'address'
                    },
                    {
                        id: '24',
                        name: '红茶df',
                        type: 'fruit'
                    }
                ],
                edges: [
                    {
                        source: '1',
                        target: '2',
                        labelInfo: {
                            payload: 1024
                        }
                    },
                    {
                        source: '2',
                        target: '1',
                        labelInfo: {
                            payload: "回头"
                        }
                    },

                    {
                        source: '2',
                        target: '3',
                        labelInfo: {
                            payload: 1024
                        }
                    },
                    {
                        source: '2',
                        target: '4',
                        labelInfo: {
                            payload: 1024
                        }
                    },
                    {
                        source: '4',
                        target: '5',
                        labelInfo: {
                            payload: 1024
                        }
                    },
                    {
                        source: '5',
                        target: '4',
                        labelInfo: {
                            payload: 1024
                        }
                    },
                    {
                        source: '5',
                        target: '6',
                        labelInfo: {
                            payload: 1024
                        }
                    }
                    ,{
                        source: '6',
                        target: '7',
                        labelInfo: {
                            payload: 1024
                        }
                    }
                    ,{
                        source: '7',
                        target: '8',
                        labelInfo: {
                            payload: 1024
                        }
                    },
                    {
                        source: '8',
                        target: '9',
                        labelInfo: {
                            payload: 1024
                        }
                    },        {
                        source: '9',
                        target: '10',
                        labelInfo: {
                            payload: 1024
                        }
                    }
                    ,{
                        source: '10',
                        target: '11',
                        labelInfo: {
                            payload: 1024
                        }
                    },
                    {
                        source: '11',
                        target: '12',
                        labelInfo: {
                            payload: 1024
                        }
                    },
                    {
                        source: '12',
                        target: '13',
                        labelInfo: {
                            payload: 1024
                        }
                    }
                    ,{
                        source: '13',
                        target: '14',
                        labelInfo: {
                            payload: 1024
                        }
                    },
                    {
                        source: '14',
                        target: '15',
                        labelInfo: {
                            payload: 1024
                        }
                    },
                    {
                        source: '15',
                        target: '16',
                        labelInfo: {
                            payload: 1024
                        }
                    }
                    ,{
                        source: '16',
                        target: '17',
                        labelInfo: {
                            payload: 1024
                        }},
                    {
                        source: '17',
                        target: '1',
                        labelInfo: {
                            payload: 1024
                        }
                    }
        

                ]
            },

            jsPlumbInstance: "", // 画线实例
            // jsPlumb默认配置
            jsPlumbSetting: {
                Container: "relation-box",
                // 连线的样式 StateMachine、Flowchart
                Connector: ["Bezier", { curviness: 100 }],
                // 鼠标不能拖动删除线
                ConnectionsDetachable: false,
                // 删除线的时候节点不删除
                DeleteEndpointsOnDetach: false,
                // 连线的端点
                Endpoint: ["Dot", { radius: 3 }],
                PaintStyle: { stroke: "#c0c4ca", strokeWidth: 1 },
                EndpointStyle: {
                    stroke: "#888",
                    fill: "#fff"
                }, ConnectionOverlays: [
                    [ "Arrow", {
                        location: 1,
                        id: "arrow",
                        length: 14,
                        foldback: 0.8
                    } ]
                    //连接点中间会出现关于连接线的说明
                   
                ],
            },
            jsPlumbConnectOptions: {
                isSource: true,
                isTarget: true,
                // 动态锚点、提供了4个方向 Continuous、AutoDefault
                anchor: "AutoDefault"
            },


            nodeList: [],
            lineList: [],
            linkConnect:{},
            nodeMap:new Map,
            nodeWidth:"180px",
            nodeHeight:"206px"
        }
    },
    watch: {
        sortFuntion() {
            this.setNodeInfo();
        }
    },
    methods: {


        layout() {

            if(this.sortFuntion==1){
                this.nodeList=  ForceDirected(1920,1080,this.root.nodes,this.root.edges)
                this.lineList=  this.root.edges
                const that=this;

                this.nodeList= this.nodeList
                    .map((s) => {
                        const data={  data: s,
                            x:s.x,
                            y:s.y,
                            width: this.nodeWidth,
                            height: this.nodeHeight,}
                        that.nodeMap.set(s.id,data)
                        return data;
                    })
                ;
            }

            if(this.sortFuntion==0){

                const g = new dagreD3.graphlib.Graph();

                g.setGraph({
                    rankdir: 'LR',
                    align: 'DR',
                    ranksep: 30,
                    width: 1920,
                    height: 1080,
                });

                const nodes= this.root.nodes
                    .map((s) => {
                        return {
                            data: s,
                            x: 0,
                            y: 0,
                            width: 180+180,
                            height: 206+30,
                        };
                    })
      ;

                nodes.forEach((d) => {
                    g.setNode(String(d.data.id), d);
                });
                this.root.edges.forEach((u) => {
                    g.setEdge(String(u.source), String(u.target), {
                        source: g.node(u.source),
                        target: g.node(u.target),
                    });
                });

                dagreD3.dagre.layout(g);

                const that=this;

         


                this.nodeList=nodes
                
                this.nodeList= this.nodeList
                    .map((s) => {


                        const data={  data: s.data,
                        
                            x:s.x,
                            y:s.y,
                            width: this.nodeWidth,
                            height: this.nodeHeight,}
                        that.nodeMap.set(s.data.id,data)
                        return data;
                    })
                ;
                this.lineList=this.root.edges;//g.edges().map((e) => g.edge(e))
            }

        },

        setNodeInfo() {
            this.layout()
            // 设置节点位置信息
            this.nodeList = this.nodeList.map(item => {
                return {
                    id: item.data.id,
                    name: item.data.name,
                    left: item.x  + "px", 
                    top: item.y + "px"
                };
            });

            const that=this
            this.lineList = this.lineList.map(item => {

                let    source;
                let    target;
                let    label;
              
                source= `node-${  that.nodeMap.get(item.source).data.id}`;
                target= `node-${that.nodeMap.get(item.target).data.id}`
                label=item.labelInfo.payload+""
                


                return {
                    source: source,
                    target:target,
                    overlays: [[ "Label", {id: "info", label:label	,cssClass:"aLabel",location:0.25,} ]]
                }
            })
        },
        updateData()
        {
            //获取数据，这里依然用root数据模拟
				

            let map = {}
            this.root.nodes.forEach(row => {
                map[row.id] = {name: row.name}
            })
            for(let node of 	this.nodeList )
            {
                node.name=map[node.id].name+"xxx"
            }
            let LinkMap = {}
            this.root.edges.forEach(row => {
                LinkMap[row.source+"_"+row.target] = {labelInfo: row.labelInfo}
            })
            
            for(let link of 	this.lineList )
            {

                // link.labelInfo=LinkMap[link.source+"_"+link.target]
               
                this.linkConnect[link.source+"_"+link.target].getOverlay("info").setLabel( Math.random().toFixed(2)+"");
               
              
            }
         
    

            this.jsPlumbInstance.repaintEverything(); // 重绘


        },
        drawLines() {
            this.$nextTick().then(() => {
                jsPlumb.ready(() => {
                    this.jsPlumbInstance = jsPlumb.getInstance();

                    this.jsPlumbInstance.importDefaults(this.jsPlumbSetting);

                    this.lineList.forEach(item => {
                        let connect=  this.jsPlumbInstance.connect(item, this.jsPlumbConnectOptions);
                        this.linkConnect[item.source+"_"+item.target]=connect
                    });

                    this.jsPlumbInstance.repaintEverything(); // 重绘

                    for(var i=0;i<this.nodeList.length;i++)
                    {
                        const node = this.nodeList[i]
                        this.jsPlumbInstance.draggable('node-'+node.id)
                    }



                })
            })
        }
    },
    mounted() {
        this.setNodeInfo();
        this.drawLines();
        this.timer = setInterval(this.updateData, 1000);
    },beforeDestroy() {
        clearInterval(this.timer);
    }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#relation-box {
  position: relative;
}

.node {
  position: absolute;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 20px 30px;
}
</style>