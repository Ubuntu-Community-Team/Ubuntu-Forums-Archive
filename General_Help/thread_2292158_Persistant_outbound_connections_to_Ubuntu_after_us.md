---
title: "Persistant outbound connections to Ubuntu after using Software Center"
date: 2015-08-25
forum: General Help
---

### Post by drm200 on 2015-08-25
I'm using Trusty 14.04 with all the latest revisions.   I notice that sometimes I have 150 - 200 outbound connections to myapps.developer.ubuntu.com.

The connections remain in the state "close_wait" forever ....  The only way I can get rid of them is reboot.

The connections appear only when I am using the Ubuntu Software Center.  When I close the Software Center the connections persist ... 

I can see the connections with this command:  
     sudo netstat -tupa | grep gvfsd-http

This is an example output.  There were 178 similar connections!

tcp        1      0 192.168.69.80:51217     myapps.developer.u:http CLOSE_WAIT  10111/gvfsd-http
tcp        1      0 192.168.69.80:60704     myapps.developer.u:http CLOSE_WAIT  10111/gvfsd-http
tcp        1      0 192.168.69.80:51221     myapps.developer.u:http CLOSE_WAIT  10111/gvfsd-http
tcp        1      0 192.168.69.80:51219     myapps.developer.u:http CLOSE_WAIT  10111/gvfsd-http
tcp        1      0 192.168.69.80:60701     myapps.developer.u:http CLOSE_WAIT  10111/gvfsd-http

This appears to be an issue that has been around since 2009 so I don't hope for any fix coming thru.   But for me this is a security issue.

I'd like to know if there is a method I can use now, that will stop the connections without going thru a reboot.

---

### Post by TheFu on 2015-08-26
Is using synaptic or aptitude or apt-get an option?

What is gvfsd-http used for?  WebDAV?  I don't know. [https://stackoverflow.com/questions/12886339/does-anybody-know-what-is-gvfsd-http](https://stackoverflow.com/questions/12886339/does-anybody-know-what-is-gvfsd-http) says it is for showing all those images in software center.

---

### Post by coldraven on 2015-08-26
+1 for Synaptic

---

### Post by ian-weisser on 2015-08-26
> **drm200 said:**
> I'm using Trusty 14.04 with all the latest revisions.   I notice that sometimes I have 150 - 200 outbound connections to myapps.developer.ubuntu.com.

The connections remain in the state "close_wait" forever ....  The only way I can get rid of them is reboot.

The connections appear only when I am using the Ubuntu Software Center.  When I close the Software Center the connections persist ... 

Since this problem can be reproduced, please file a bug report.
The USC developers did not, I'm sure, intend that behavior.

---

### Post by drm200 on 2015-08-26
This is an old problem ... I found complaints going back to 2005.   There have been at least two previous bug reports (571970 and 760344).  I added my information to both before asking for help here .... 

I would really like to find a command that would kill the connections without reboot.  Restarting network manager has not impact.

---

### Post by drm200 on 2015-08-26
"[COLOR=#000000]Is using synaptic or aptitude or apt-get an option?"[/COLOR]

I'm hoping someone can offer a command that would allow me to kill the connections without reboot.  That would be my preferred remedy.   If not I'll look at Synaptic ... I've never used it.

apt-get is not such a good option for me.   I've always been prone to typos ... and now I must consider "senior moments" on top of that ... So I prefer to avoid the command line if at all possible.
When I do use the command line I use cut and paste of pre-used lines if at all possible just to avoid mistakes..

thanks

---

### Post by TheFu on 2015-08-26
I use select/paste all the time 
AND
tab completion.  If you find yourself typing more than 3 characters at a time you are doing it the hard way. Probably the best way to learn this is by watching a youtube video if you don't hang out with other Linux people in-person.

**ifdown** should kill all network connections on the interface provided in the cmd-options. Use **ifup** to bring it up.

---

### Post by drm200 on 2015-08-28
> **TheFu said:**
> I use select/paste all the time 
AND

**ifdown** should kill all network connections on the interface provided in the cmd-options. Use **ifup** to bring it up.

Thanks ... but the command doesn't work.  I type: 
      sudo ifdown wlan0

which results in this message:  ifdown: interface wlan0 not configured  .... this seems to be another bug in Ubuntu ... as wlan0 is working fine.

I also tried sudo ifdown -a

which results in nothing ... the wireless connection is still working .... as I am posting via wlan0 here!

Anyway, if I use network manager to shutoff the wireless network and then connect again, but the connections to Ubuntu persist .... I'm still hoping to find a way to kill these connections without reboot.

---

### Post by TheFu on 2015-08-28
This  [https://stackoverflow.com/questions/15912370/how-do-i-remove-a-close-wait-socket-connection](https://stackoverflow.com/questions/15912370/how-do-i-remove-a-close-wait-socket-connection) explains how to find the process keeping those in the list.  I searched with "CLOSE_WAIT" to find that answer. Nice explanation of the issue.

Haven't tried it myself. There's a link to a github tool to find and kill processes. A mix of shell and perl.

Wifi is different from wired ethernet. Don't know much about it, but it uses other tools.

---

### Post by The Cog on 2015-08-28
Edit:
Removed erroneous posting.

---

### Post by drm200 on 2015-08-31
> **TheFu said:**
> This  [https://stackoverflow.com/questions/15912370/how-do-i-remove-a-close-wait-socket-connection](https://stackoverflow.com/questions/15912370/how-do-i-remove-a-close-wait-socket-connection) explains how to find the process keeping those in the list.  I searched with "CLOSE_WAIT" to find that answer. Nice explanation of the issue.

Haven't tried it myself. There's a link to a github tool to find and kill processes. A mix of shell and perl.

Wifi is different from wired ethernet. Don't know much about it, but it uses other tools.


I've not had any problems to find the process culprit.   It is [COLOR=#000000][FONT=Ubuntubeta]gvfsd which is being used by the Ubuntu Software Center.   I've taken a look at the githup tool ... It looks interesting but have not tried it yet as I don't have any experience on how to use a perl script.  But maybe I can figure it out.

[/FONT][/COLOR]thanks.

Am I the only one with the CLOSE_WAIT problem when using the Ubuntu Software Center?

---

