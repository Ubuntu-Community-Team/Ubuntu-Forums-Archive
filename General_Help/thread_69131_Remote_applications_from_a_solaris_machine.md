---
title: "Remote applications from a solaris machine"
date: 2005-09-25
forum: General Help
---

### Post by jfosorio on 2005-09-25
Hello, 

 I am running a remote session using xnest from a Solaris machine using as a client  my ubuntu desktop and I have a lot of problems running specifically one. The application start but works extremely slow apparently because there is a problem with the fonts that CDE uses (CDE: the solaris desktop) . (This problem do not appear when a windowsXP machine when a commercial  x client call x-win32 is used). I have installed almost all the fonts I've found in the ubuntu repositories without success.  


When I launch the application in the remote machine I get the following warning:

	Warning: Cannot convert string "-dt-interface user-medium-r-normal-s*-*-*-*-*-*-*-*-*" to type FontStruct	
	Warning: Missing charsets in String to FontSet conversion
	Warning: Cannot convert string "-dt-interface system-medium-r-normal-s*-*-*-*-*-*-*-*-*" to type FontSet
	Warning: Missing charsets in String to FontSet conversion
	Warning: Cannot convert string "-dt-interface user-medium-r-normal-s*-*-*-*-*-*-*-*-*" to type FontSet

And I get from the xnest application: 
Could not init font path element /usr/X11R6/lib/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/CID/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/CID/, removing from list!


Also, I have tried to run the application directly without a nested x client but the problem here is that Solaris do not suport UTF-8 and the application start to complain about that with messages like:

\w *WARNING* (reader): string terminated by illegal char \044 at line 4 of file /usr_cad/cadence2003/ic5.32/tools.sun4v/dfII/etc/tools/rod/.cdsenv

My setup is:
Remote machine: SunOS 5.8     
Client machine: Ubuntu  

Thanks in advance
Felipe Osorio

---

### Post by professor_chaos on 2005-09-27
I do the same thing at work, and get the same messages but the application loads anyway. 
Try moving the order of the fonts in /etc/X11/xorg.conf
Try moving "/usr/lib/X11/fonts/75dpi" to the top of the list. I think it's a problem with sun using the highest priority font and not getting to the rest.

---

### Post by jfosorio on 2005-09-27
Hello, 
Yes, the applications works, but in my case, with a highly demanding graphic application, it becomes unusable.

---

### Post by jfosorio on 2005-10-25
This do not resolve the problem, some other ideas are welcome.

---

