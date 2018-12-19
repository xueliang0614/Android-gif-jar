 将jar包拖放到libs目录。

 在JAVA文件中导入该包。

    import com.ant.liao.GifView;
    import com.ant.liao.GifView.GifImageType;

 

布局文件gif.xml： 

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
	android:orientation="horizontal"												android:layout_width="fill_parent"												android:layout_height="fill_parent">
 
		
	
	 <com.ant.liao.GifView
		android:id="@+id/gif1" 
		android:layout_height="wrap_content" android:layout_width="wrap_content"
		android:paddingRight="14px" android:enabled="false" />
	<TextView android:id="@+id/tsxt" android:layout_height="wrap_content" android:layout_width="wrap_content"
		android:paddingRight="4px" android:enabled="false"
		android:text="click the Angel" />	
	
	  <com.ant.liao.GifView
		android:id="@+id/gif2" 
		android:layout_height="wrap_content" android:layout_width="wrap_content"
		android:paddingTop="4px" android:paddingLeft="14px" android:enabled="false" />
 
</LinearLayout>

 

程序源码MainActivity.java：

package com.TestGif;
 
import android.app.Activity;
import android.os.Bundle;
import android.view.View;
import android.view.View.OnClickListener;
 
import com.ant.liao.GifView;
import com.ant.liao.GifView.GifImageType;
 
 
 
 
public class MainActivity extends Activity implements OnClickListener{
	
	
	private GifView gf1;	
	private GifView gf2;
	private boolean f = true;
 
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
 
        setContentView(R.layout.gif);
		gf1 = (GifView)findViewById(R.id.gif1);
		gf1.setGifImage(R.drawable.gif1);
		gf1.setOnClickListener(this);
		
		
		gf2 = (GifView)findViewById(R.id.gif2);
		gf2.setGifImageType(GifImageType.COVER);// 设置加载方式：先加载后显示、边加载边显示、只显示第一帧再显示   				gf2.setShowDimension(300, 300);		// 设置显示的大小，拉伸或者压缩		
		gf2.setGifImage(R.drawable.a);
    }
    
    
    public void onClick(View v) {
		if(f){
			gf1.showCover();
			f = false;
		}else{
			gf1.showAnimation();
			f = true;
		}
	}
    
    
    
}

