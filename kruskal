#include <stdio.h>
#define MAXVEX 10
#define TRUE 1
#define FALSE 0

typedef struct{
    int vertex1;        //存储边的起始顶点
    int vertex2;        //存储边的终止顶点
    int weight;         //权值
}Edge;

int kruskal(Edge Edges[],int n,int e)
{ 
    int i,j,v1,v2,a1,a2,k;
    int a[n+1];
    for(i=1;i<=n;i++)
        a[i]=i;
    k=1;                     
    j=0;                     //下标初值为0
   while(k<e)               //生成的边数小于e时继续循环
   {
       v1=Edges[j].vertex1;
       v2=Edges[j].vertex2; //取一条边的两个邻接点
       a1=a[v1];
       a2=a[v2];
        if(a1!=a2)    //防止出现闭合回路 
        {
            printf("(%d,%d)\n",v1,v2);
            
            k++;                //生成边数增加 
            if(k>=n)
                break;
            for(i=1;i<=n;i++) 
                if (a[i]==a2)  
                    a[i]=a1;
        }
     j++;
   }
}

int sort(Edge arr[],int low,int high)
 {
    int key;
    Edge min;
    min=arr[low];
    key=arr[low].weight;
    while(low<high)
    {
        while(low<high && arr[high].weight>=key)
            high--;
        if(low<high)
            arr[low++]=arr[high];

        while(low<high && arr[low].weight<=key)
            low++;
        if(low<high)
            arr[high--]=arr[low];
     }
     arr[low]=min;
     return low;
  } 
  
void quick_sort(Edge arr[],int start,int end)
{
    int pos;
    if(start<end)
    {
    pos=sort(arr,start,end);
    quick_sort(arr,start,pos-1);
    quick_sort(arr,pos+1,end);
    }
}

int main()
{
    Edge Edges[MAXVEX];
    int numEdges,numVertexes;
    printf("输入顶数和边数:\n");
    scanf("%d%d",&numVertexes,&numEdges);
    for(int i=0;i<numEdges;i++)
	{
    	scanf("%d%d%d",&Edges[i].vertex1,&Edges[i].vertex2,&Edges[i].weight);
	}    
    quick_sort(Edges,0,numEdges-1);
    kruskal(Edges,numVertexes,numEdges);
}
