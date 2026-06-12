---
title: "gedit doesn't recognize characters.."
date: 2008-02-11
forum: General Help
---

### Post by theodorekon on 2008-02-11
As I'm trying to learn java I wrote a small code which writes an integer on a .txt file. the code I used is the following (not that it matters..):

```

import java.io.*;

class dataOutputStream {
public static void main(String args[]) throws IOException {
	int d;
	String s;
	File f=new File("dataOutputStream");
	FileOutputStream fouts=new FileOutputStream(f);
	DataOutputStream douts=new DataOutputStream(fouts);
	d=108743;
	s=null;
	s=String.valueOf((int) d);
	System.out.println(s);
	douts.writeChars(s);
	douts.close();
	fouts.close();
}
}

```

When I open the output file with gedit I get the following incomprehensible characters as if it was binary:
> 
&#12544;&#12288;&#14336;&#14080;&#13312;&#13056;



When I read the output file with "more" it shows the correct result.
Is there some problem with the fonts in gedit or what??

PS. Please keep it simple cause I'm a newbie..

---

