---
title: "mplayer won't play .ram url"
date: 2008-06-22
forum: General Help
---

### Post by joekidston on 2008-06-22
I am having a nightmare streaming .ram files.

I have moved to Mplayer (no luck with RealPlayer)

When I type 

laptop:~$ mplayer -v -playlist [http://www.fin.ucar.edu/it/mms/webcasts/cgd/gerald_meehl.ram](http://www.fin.ucar.edu/it/mms/webcasts/cgd/gerald_meehl.ram)

result is 

MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Filename for url is now [http://www.fin.ucar.edu/it/mms/webcasts/cgd/gerald_meehl.ram](http://www.fin.ucar.edu/it/mms/webcasts/cgd/gerald_meehl.ram)
Filename for url is now [http://www.fin.ucar.edu/it/mms/webcasts/cgd/gerald_meehl.ram](http://www.fin.ucar.edu/it/mms/webcasts/cgd/gerald_meehl.ram)
STREAM_HTTP(1), URL: [http://www.fin.ucar.edu/it/mms/webcasts/cgd/gerald_meehl.ram](http://www.fin.ucar.edu/it/mms/webcasts/cgd/gerald_meehl.ram)
Resolving [www.fin.ucar.edu](www.fin.ucar.edu) for AF_INET6...
[B]Couldn't resolve name for AF_INET6: [www.fin.ucar.edu](www.fin.ucar.edu)
[/B]

Does anyone have any ideas?  Should I post up more of the terminal output (there are loads more lines of output...)

Cheers
Joe

---

### Post by joekidston on 2008-06-22
the last few lines of output are 

Resolving [www.fin.ucar.edu](www.fin.ucar.edu) for AF_INET6...
Couldn't resolve name for AF_INET6: [www.fin.ucar.edu](www.fin.ucar.edu)
Resolving [www.fin.ucar.edu](www.fin.ucar.edu) for AF_INET...
Connecting to server [www.fin.ucar.edu](www.fin.ucar.edu)[128.117.71.218]: 80...
--- HTTP DEBUG HEADER --- START ---
protocol:           [HTTP/1.1]
http minor version: [1]
uri:                [(null)]
method:             [(null)]
status code:        [404]
reason phrase:      [Not Found]
body size:          [292]
Fields:
 0 - Date: Sun, 22 Jun 2008 08:45:47 GMT
 1 - Server: Apache
 2 - Content-Length: 292
 3 - Connection: close
 4 - Content-Type: text/html; charset=iso-8859-1
--- HTTP DEBUG HEADER --- END ---
Server returned 404: Not Found
No stream found to handle url [http://www.fin.ucar.edu/it/mms/webcasts/cgd/--stop--](http://www.fin.ucar.edu/it/mms/webcasts/cgd/--stop--)

vo: x11 uninit called but X11 not inited..

---

### Post by manfer on 2008-06-22
Those ones are not audio streaming ram files.

They are SMIL multimedia presentation ram files. I wasn't able to play then either.

If you look what is on those ram files you would see they only contains a link to a SMI file.

---

### Post by manfer on 2008-06-22
Installing real player 11 you can play them. Go to realplayer for linux page:

[http://www.real.com/linux](http://www.real.com/linux)

Press Download Realplayer button to obtain the bin installer.

Open a terminal and go to the location where you downloaded the installer and type:

prompt:~$ **sudo chmod +x RealPlayer11GOLD.bin**
prompt:~$ **sudo ./RealPlayer11GOLD.bin**

and follow instructions the installer shows you. The default options are good ones so easy to make the installation.

Then you would be able to play those files. Open Applications -> Sound & Video -> RealPlayer 11 and use File -> Open URL to play files.

I'm looking if now firefox can be configured to open realplayer 11 to play them.

---

### Post by joekidston on 2008-06-22
Thank you very much for the reply - Yes, I (finally) managed to get the .ram files to play in RealPlayer (I can't get FireFox to launch RealPlayer, it always defaults to Totem, but when I followed your instructions, RealPlayer opened them fine).  

I was hoping to store them on my system from home, then watch them at work (our institution blocks .ram files), but don't think I can do that with RealPlayer...

Thanks again.
Joe

---

