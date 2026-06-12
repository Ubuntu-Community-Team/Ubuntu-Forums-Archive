---
title: "Compression using all cores"
date: 2016-07-30
forum: General Help
---

### Post by 4kh3RAm on 2016-07-30
Does this mean that 7zip will automatically use 4 cores when compressing and decompressing files ?
```

7-Zip (A) [64] 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18
p7zip Version 9.20 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,4 CPUs)
```

---

### Post by nikefalcon on 2016-07-31
A quick test using **p7zip** uses only up to 50% CPU on my 4 core machine, so I'm not sure what the answer is. It'l depend on how the compression algorithm you are using has been implemented.
More info here:
[https://superuser.com/questions/433945/multithreaded-support-in-7za](https://superuser.com/questions/433945/multithreaded-support-in-7za)
[URL="https://superuser.com/questions/142021/7-zip-compression-on-multi-core-computers"]https://superuser.com/questions/142021/7-zip-compression-on-multi-core-computers
[/URL]
EDIT:
The following works as expected.
```

7za a -tzip Courses.zip Courses -mmt=1
7za a -tzip Courses.zip Courses -mmt=2

```
However, setting mt=3 and higher has no effect; 7z seems to be limited to 2 threads only.

If you absolutely must use 7zip instead of other compression algs that are multithreaded; look into gnu **parallel.**

---

### Post by howefield on 2016-07-31
As I understand it, multi thread support defaults to on with p7zip.

You could always test it by watching the cpu cores via htop whilst creating an archive, eg, as per the attached image.

---

### Post by sudodus on 2016-07-31
I think there is good information at

[https://askubuntu.com/questions/258202/multi-core-compression-tools](https://askubuntu.com/questions/258202/multi-core-compression-tools)

and you find more links, if you browse the internet for **linux multithread compression**

---

### Post by 4kh3RAm on 2016-07-31
I found out that 7zip automatically uses all cores.
 	Quote:
 	[TABLE="width: 100%"]
 	[TR]
 		[TD="class: bbcodeblock"] 			 				7-Zip [64] 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18
p7zip Version 9.20 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,_4 CPUs_) 			 		[/TD]
 	[/TR]
 	[/TABLE]
 
And both top and htop show all four CPUs being used.

---

