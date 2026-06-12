---
title: "Missing ssh.h file in make"
date: 2018-07-29
forum: General Help
---

### Post by Vaclav Vasek on 2018-07-29
I am installing (SSH) TCF Agent on Raspberry Pi using this procedure 
  	 	 	 	   [h=1][https://wiki.eclipse.org/TCF/Raspberry_Pi](https://wiki.eclipse.org/TCF/Raspberry_Pi)[/h]This process worked fine on Raspbian OS , but fails on new clean install of MATE
 
It stopped "make"  because it not find a file - ssh.h. 

What would be easiest way to correct this ?

Here are MY preferred options:

Find where Ubuntu MATE keeps ssh.h? 
Find where make expect it and move copy MATE ssh.h file there? 
Modify make to point to MATE installed ssh.h file ? 

Thanks

---

