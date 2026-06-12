---
title: "Loading Cannon MX860 Drivers"
date: 2013-08-11
forum: General Help
---

### Post by mcman56 on 2013-08-11
Multiple times in the past I have loaded MX860 Drivers using the method below from:  [http://ubuntuforums.org/showthread.php?t=1488850&highlight=mx860+kubuntu&page=2](http://ubuntuforums.org/showthread.php?t=1488850&highlight=mx860+kubuntu&page=2)

I'm  now trying this on a Gateway NE71B with 12.04 but it is not working.   When clicking the downloaded items, it takes me to the software center  to load and offers an INSTALL option.  When clicking this, it appears to  install but then goes right back the the screen with INSTALL option.  See attached pic.  When doing this in the past, I beleive I just clicked on the file and it loaded with no trip to the software center.[ATTACH=CONFIG]245274[/ATTACH] 		 		 		 		[h=2]Re: Canon MX printer installtion on Kubuntu Lucid 10.04 AMD64[/h] 		 				 				 		 			 				[INDENT] 					[FONT=Trebuchet MS][SIZE=2][COLOR=Navy]Excellent  thread and work; very helpful.  I had explored the same about a year  ago and the following has worked for me several times after performing  clean Ubuntu installs including Ubuntu 10.10.  I too have a Canon MX860 configured wirelessly.  The procedure is similar to the original post, just slightly simpler:

[SIZE=3]Go to the Canon site in Australia and download the [Linux debian driver for the MX860]("http://pdisp01.c-wss.com/gdl/WWUFORedirectTarget.do?id=MDEwMDAwMTg3NzAx&cmp=ABS&lang=EN").  After unpackaging the compressed driver:
[/SIZE][/COLOR][/SIZE][/FONT][INDENT][FONT=Trebuchet MS][SIZE=3][COLOR=Navy]1. First, install cnijfilter-common_3.10-1_i386.deb[/COLOR][/SIZE][/FONT][SIZE=3]

[/SIZE][FONT=Trebuchet MS][SIZE=3][COLOR=Navy]2. Second, install cnijfilter-mx860series_3.10-1_i386.deb[/COLOR][/SIZE][/FONT][SIZE=3]

[/SIZE][FONT=Trebuchet MS][SIZE=3][COLOR=Navy]3. Restart Ubuntu[/COLOR][/SIZE][/FONT][SIZE=3]

[/SIZE][FONT=Trebuchet MS][SIZE=3][COLOR=Navy]4. System -> Adminstration -> Printing -> New[/COLOR][/SIZE][/FONT]
[FONT=Trebuchet MS][SIZE=2][COLOR=RoyalBlue]It should search for and find the Canon- MX860 printer as a Network Printer with a device URI that looks like: cnijnet:/00-1E-8F-72-E6-2H[/COLOR][/SIZE][/FONT][/INDENT]
[SIZE=2][COLOR=Navy]Using the procedure above, both the printing and scanning functions work for me on the MX860.[/COLOR][/SIZE] 				[/INDENT]

---

