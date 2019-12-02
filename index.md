## 稀疏数组

稀疏数组的特点是什么？为什么要提出稀疏数组的概念？

	1.稀疏数组的特点是第一行记录原始数组的行数、列数、有效数据个数，余下的行记录原始数组中有效数据的行、列、值
	2.稀疏数组是一种压缩二维数组的形式，它能够把数组的内容压缩，使得空间利用率增大
	
稀疏数组代码实现：

public class SparseArray {

	//本clsaa的内容：

	/*
		*将一个数组转化成稀疏数组
		*将转化好的稀疏数组再转化回来
		*将上内容全部打印出来 
	 */
 

	public static void main(String[] args) {
		// TODO 自动生成的方法存根
		int[][] chess;
		chess = new int[11][11];
		chess[1][2] = 1;
		chess[2][3] = 2;
		chess[4][5] = 1;
		chess[9][10] = 2; 
		
		for(int[] row : chess) {
			for(int data : row) {
				System.out.printf("%d\t",data);
			}
			System.out.println();
		}
		
		int count = 0;
		for(int[] row : chess) {
			for(int data : row) {
				if(data != 0) count++;
			}
		}
		
		//System.out.println(count);
		
		int[][] sparseArray;
		int num = 1;
		sparseArray = new int[count + 1][3];
		sparseArray[0][0] = sparseArray[0][1] = 11;
		sparseArray[0][2] = count;
		
		for(int i = 0; i < 11; i++) {
			for(int j = 0; j < 11; j++) {
				if(chess[i][j] != 0) {
					sparseArray[num][0] = i;
					sparseArray[num][1] = j;
					sparseArray[num][2] = chess[i][j];
					num++;
				}
			}
		}
		
		for(int[] row : sparseArray) {
			for(int data : row) {
				System.out.printf("%d\t", data);
			}
			
			System.out.println();
		}
		
		
		int[][] chessArray;
		
		chessArray = new int[sparseArray[0][0]][sparseArray[0][1]];
		
		for(int[] row : chessArray) {
			for(int data : row) {
				data = 0;
			}
		}
		
		for(int i = 0; i < count; i++) {
			chessArray[ sparseArray[i + 1][0] ][ sparseArray[i + 1][1] ] = sparseArray[i + 1][2];
		}
		
		
		for(int[] row : chessArray) {
			for(int data : row) {
				System.out.printf("%d\t", data);
			}
			
			System.out.println();
		}
		
	}

}

