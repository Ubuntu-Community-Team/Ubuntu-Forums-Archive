---
title: "Disabling Automatic Teamview logged in status, on startup"
date: 2013-12-22
forum: General Help
---

### Post by Camy on 2013-12-22
Hi All
I noticed that as soon as my Ubuntu machine has booted I get a notification on my work machine that I've logged in, even though Teamviewer was not started. I assumed that there must be a service for this, so I installed a few service checking programs like (chkconfig, jobs-admin) , but I cound not see anything related to teamviewer. I was expecting a service name with teamSOMETHING, or viewerSOMETHING.
Does anyone know how I could turn this off.
Thanks

---

### Post by ian-weisser on 2013-12-22
Teamviewer is not in the Ubuntu repositories. Support for non-Ubuntu software is generally done by the developer, not the Ubuntu community.
Have you asked Teamviewer support?

---

### Post by bapoumba on 2013-12-22
Please have a look here, this user had auto login and lost admin privilege to his two accounts. He said it was after using Teamviewer, see post #7.
[http://ubuntuforums.org/showthread.php?t=2193917](http://ubuntuforums.org/showthread.php?t=2193917)

---

### Post by Camy on 2013-12-23
No I haven't Ian, because I thought it was something easy like just disabling the service. I'll ask there.
Thanks

---

### Post by Camy on 2013-12-23
[**[COLOR=#C61919][B]Hi bapoumba**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=171805"), I think I did not explain well enough. Teamviewer isn't logging in as a user into Ubuntu. What it does is register on the internet that I have switched my Ubuntu pc on. So I was assuming that a service is being started that is sending this info. I would like to switch that off, until I actually open teamviewer.  
Thanks

---

### Post by bapoumba on 2013-12-23
Hello Camy, you did explain well, and I did understand. I probably was not clear :)
I pointed you at the thread because the user had much troubles after running teamviewer, so I just wanted to warn you and give you the opportunity to have it handy in case things also went wrong on your side.

After some research, here are a couple links that may help you investigate :
[http://ubuntuforums.org/showthread.php?t=2092298](http://ubuntuforums.org/showthread.php?t=2092298) > post #2 has some daemon commands
[http://ubuntuhandbook.org/index.php/2013/11/show-all-hidden-startup-applications-ubuntu1310/](http://ubuntuhandbook.org/index.php/2013/11/show-all-hidden-startup-applications-ubuntu1310/) > show hidden startup applications (not tested).

Cheers!
b.

---

### Post by Camy on 2013-12-23
[ 						 							 						 					]("http://ubuntuforums.org/member.php?u=171805") 				 				 					 						 	[**[COLOR=#C61919][B]bapoumba**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=171805")  	 great thanks. Had a look at the threads you recommended but the daemon commands return an error. Don't know if it's to do with the teamviewer version I am using ie version 6. It seems to work through wine. 
I did find the startup applications link very helpful as I managed to get rid of a lot of services that I was not using via this [link]("http://www.hecticgeek.com/2012/06/few-things-to-speed-up-ubuntu/").
I'll try and ask teamviewer about it, when I get some extra time.
Thanks

---

### Post by bapoumba on 2013-12-23
> **Camy said:**
> [ 						 							 						 					]("http://ubuntuforums.org/member.php?u=171805") 				 				 					 						 	[**[COLOR=#C61919][B]bapoumba**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=171805")  	 great thanks. Had a look at the threads you recommended but the daemon commands return an error. Don't know if it's to do with the teamviewer version I am using ie version 6. It seems to work through wine. 
Probably. I was not quite sure it would work. There are other posts in the thread, but not having teamviewer, I cannot troubleshoot. I should add that I run on macs at work, and tried it there some time ago. It was not working very well from my perspective, lots of logouts and hang ups. May be I should try a newer version, but we use either a commercial standalone app now or a plugin in our moodle site.
> **Camy said:**
> [ I did find the startup applications link very helpful as I managed to get rid of a lot of services that I was not using via this [URL="http://www.hecticgeek.com/2012/06/few-things-to-speed-up-ubuntu/"]link]("http://ubuntuforums.org/member.php?u=171805").
I'll try and ask teamviewer about it, when I get some extra time.
Thanks
You are most welcome :)

---

