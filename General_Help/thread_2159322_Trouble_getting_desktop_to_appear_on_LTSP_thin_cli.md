---
title: "Trouble getting desktop to appear on LTSP thin client after login"
date: 2013-07-02
forum: General Help
---

### Post by zerubbabel on 2013-07-02
I carefully followed the procedure on this page: 

[http://www.thefanclub.co.za/how-to/how-create-ubuntu-1104-x64-ltsp-server-32bit-thin-clients]("http://www.thefanclub.co.za/how-to/how-create-ubuntu-1104-x64-ltsp-server-32bit-thin-clients")

for my LTSP installation on a clean install of Ubuntu 12.04 LTS. The only thing I did differently is use 192.168.0.1 for eth1, which is my client-side network, and also I did not do the optional steps 6a and 6b. 

When I boot from a thin client, I get the login splash screen, and if I try to login using the test userid I created in step 9, it says "No response from server, restarting..." and I'm back at the login screen. 

If I log in using my regular login on the server, the login succeeds, but it doesn't get past the empty screen with the multi-colored orange/pink/purple background. 

After a little while, I do Ctrl-Alt-Del on the client and a dialog box appears allowing me to logout, but no desktop ever appears. 

Also, after the successful login (but no desktop), Compiz crashes on the server desktop. 

I'd very much appreciate any help getting past this point. This is my first attempt at setting up an LTSP server/client computer lab.

---

### Post by zerubbabel on 2013-07-02
I got around the desktop problem by choosing the 2D desktop before logging in. That worked fine when logging in under my regular server login account. I could run Firefox and LibreOffice on the client. It would be nice it 2D was the default, so I wouldn't have to select it each time. I suppose that's settable in configuration file somewhere.

However, trying to login on the test account I created in step 9 of the "how-to"instructions still resulted in "No response from server, restarting..." although I was able to log in using that account when logging in directly on the server machine, so I know the password is correct.

---

