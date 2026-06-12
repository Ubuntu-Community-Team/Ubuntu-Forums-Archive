---
title: "Post Remote desktop problems"
date: 2012-11-15
forum: General Help
---

### Post by ksp1717 on 2012-11-15
Hi 

I am using 12.04 on a laptop. I am able to connect and run the required programs in ubuntu from a Win7 laptop using xrdc. 

I do not see the programs which are already running on the desktop.

After I quit the remote connection in the windows laptop, and when I login into the ubuntu desktop I dont see the programs which I have opened from the remote connection and which were supposed to be running. 


I looked in the System Monitor > Processes and found all the applications which I have opened over there, but the %CPU column of all these show 0. I am not to open the programs like browser (firefox, chrome) as long as it is in the Processes. 

Can anyone help me understand what is going on here and how to fix it because the remote connection is of no use if the programs do not run after I close the remote connection.

Thanks

ksp

---

### Post by ksp1717 on 2012-11-15
Ok after searching for a while I found [this]("http://scarygliders.net/2012/06/20/x11rdp-o-matic-and-rdpsesconfig-version-2/").

I used the script in there and after it finished executing, I tried logging in. 

It has solved part of the problem. Now all the remote logins go into one session (no matter which computer I connect from all the remote connections take me to one single session) but I cannot login into the same session on the server. 

In short, I have one session for all remote logins and one session for the actual login on the server side of the _same user_.

Any ideas how to get over this?

ksp

---

