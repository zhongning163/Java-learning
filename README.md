# Java-learning
小白的第一天
/*
将一个数转换为十六进制，如60
将60的二进制码0000-0000 0000-0000 0000-0000 0011-1100与15进行&运算
			  0000-0000 0000-0000 0000-0000 0000-1111（15），目的是为了将目标数的最低4位提出来，然后再将目标数向右移四位，继续进行&运算
什么时候使用数组？如果数据出现了对应关系，且对应关系的一方是有序的数字编号，且作为角标使用，这时就想到数组的使用
就可以将数据存在数组里，根据运算的结果作为角标直接去查数组中对应的元素即可

这种方法叫做：查表法
*/

class TableToHex
{
	public static void main(String[] args)
	{	
		char[] arr={'0','1','2','3',		//定义一个对应关系表
			          '4','5','6','7',
			          '8','9','A','B',
			          'C','D','E','F'};
		toHex(arr,60);
	}

	public static void toHex(char[] arr,int num)
	{
		for(int x=0;x<8;x++)				//一个数中最多8个字节，进行八次循环
		{
			int temp=num&15;				//15对应的二进制是1111，用它来“与”来获得最低四位，并赋给临时变量temp
			/*if(temp>=0&&temp<=9)			//如果temp是0-9，就直接输出
				System.out.println(temp);
			else
				System.out.println(arr[temp-10]);			//如果不是0-9，就转换成A-F输出
			*/
			System.out.println(arr[temp]);
			num=num>>>4;									//进行无符号右移来获取较高的4位
		}
	}
}
