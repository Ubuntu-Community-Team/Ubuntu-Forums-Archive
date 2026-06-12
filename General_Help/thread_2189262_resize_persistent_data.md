---
title: "resize persistent data"
date: 2013-11-21
forum: General Help
---

### Post by tendouser on 2013-11-21
Is it possible to resize persistent data file casper for lubuntu?
I noted that LiLi created the file but with a max 4GB size!

Cheers!

---

### Post by tendouser on 2013-11-21
is this right to do?

 			 				 				 					 						 	[**[COLOR=#000000]geirha[/COLOR]**]("http://ubuntuforums.org/member.php?u=243323") 	 
 						[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]  					 					 						Ubuntu addict and loving it 					 					 						[IMG]http://ubuntuforums.org/images/rank_27.png[/IMG] 					                                           					 					 						 							     						
 					 				
 			
 			 				 					Join DateFeb 2007Beans4,045DistroUbuntu 9.10 Karmic Koala 					 					 				
 			 		
 	  	 		 		 		 		[h=2]Re: Resize Casper-rw file (persistent store of ubuntu on usb pendrive)?[/h] 		 				 				 		 			 				[INDENT] 					You can also resize the filesystem.  First, you need to extend the image file to the desired size. If you  want increase the size from 500MB to 1GB, you'll need to add 500MB of  zeroes to the end of the file.

It's a good idea to backup the image first.

1. add 500MB of zeroes to the end of the image casper-rw. Make sure you use >> (append) and not > (overwrite).
 	Code:
 	dd if=/dev/zero bs=1M count=500 >> casper-rw 
2. resize the filesystem to cover the entire image file
 	Code:
 	resize2fs casper-rw 
That should be it. 				[/INDENT] 			
  			   		
 			 				 			 			 			 		
 	
If so can I append 2GB more like this?
dd if=/dev/zero bs=1M count=2000 >> casper-rw

---

### Post by tendouser on 2013-11-21
[https://github.com/jtriley/StarCluster/issues/168](https://github.com/jtriley/StarCluster/issues/168)

there you go boyz!!

cheers!

---

