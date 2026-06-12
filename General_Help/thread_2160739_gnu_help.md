---
title: "gnu help"
date: 2013-07-08
forum: General Help
---

### Post by priyaanand on 2013-07-08
hi everyone
I'm a newbie in ubuntu.I have installed gnustep on my ubuntu  but I see problems executing my objective-c codes.What is the general command to complie an objective-c code with gnustep on ubuntu?

TIA

---

### Post by dino99 on 2013-07-08
[https://www.google.fr/#q=ubuntu+gnustep+compiling&source=lnt&tbs=qdr:y&sa=X&ei=xoTaUaPYN8SZhQeXh4HABQ&ved=0CBkQpwUoBQ&bav=on.2,or.r_qf.&fp=2049875acbfb0313&biw=1674&bih=925](https://www.google.fr/#q=ubuntu+gnustep+compiling&source=lnt&tbs=qdr:y&sa=X&ei=xoTaUaPYN8SZhQeXh4HABQ&ved=0CBkQpwUoBQ&bav=on.2,or.r_qf.&fp=2049875acbfb0313&biw=1674&bih=925)

---

### Post by priyaanand on 2013-07-08
Thank you dino99.I tried to compile a simple hello world code.I tried compiling using " gcc `gnustep-config --objc-flags` -lgnustep-base hello.m -o hello".I then get the following errors:

hello.m:5: error: undefined reference to 'objc_get_class'
hello.m:5: error: undefined reference to 'objc_msg_lookup'
hello.m:5: error: undefined reference to 'objc_msg_lookup'
hello.m:9: error: undefined reference to 'objc_msg_lookup'
hello.m:11: error: undefined reference to '__objc_exec_class'
collect2: ld returned 1 exit status

TIA

---

### Post by priyaanand on 2013-07-08
Hi I solved the issue using
"gcc practice.m practicemain.m `gnustep-config --objc-flags` -lobjc -lgnustep-base -o practicemain"

practicemain.m:file with "main" function
practice.m:file with the implemnentation of whatever class I used

ThankYou.

---

