---
title: "[SOLVED] vsftpd help?"
date: 2008-06-29
forum: General Help
---

### Post by vanflyheight13 on 2008-06-29
Can someone tell me where I put the files I want to be accessible?

I know it sounds noob-ish, but I'm just about getting used to linux now.
Got everything configured the way I like it and I'm finding it a lot easier than I expected it to be. :)

---

### Post by Mikecore on 2008-06-29
> **vanflyheight13 said:**
> Can someone tell me where I put the files I want to be accessible?

I know it sounds noob-ish, but I'm just about getting used to linux now.
Got everything configured the way I like it and I'm finding it a lot easier than I expected it to be. :)

[https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html)

---

### Post by vanflyheight13 on 2008-06-29
> **Mikecore said:**
> [https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html)

Maybe it's the time of morning, but I just don't see how that helps me.. :confused:

---

### Post by manfer on 2008-06-29
/home/ftp ?????????

That is if you only need anonymous.

If you want to configure users it is better to read the manual or maybe someone could help. I haven't configured for users.

But for anonymous just put your files in /home/ftp

---

### Post by vanflyheight13 on 2008-06-29
> **manfer said:**
> /home/ftp ?????????

I thought it was that obvious, but my files are not showing there when I view through Firefox. :confused:

---

### Post by manfer on 2008-06-29
???

What do you put in firefox to try to enter the ftp?

To test it in same computer try:

[ftp://localhost](ftp://localhost)

and from any other computer on network or the same computer:

[ftp://localIP/](ftp://localIP/)

---

### Post by vanflyheight13 on 2008-06-29
> **manfer said:**
> ???

What do you put in firefox to try to enter the ftp?

To test it in same computer try:

[ftp://localhost](ftp://localhost)

and from any other computer on network or the same computer:

[ftp://localIP/](ftp://localIP/)

[ftp://86.xxx.xxx.xxx.](ftp://86.xxx.xxx.xxx.) is the way I'm trying to access it.

[ftp://localhost/](ftp://localhost/) works absolutely fine and shows all my files, but when I try to access it through the [ftp://IP](ftp://IP) / method I just get an page with no files.

---

### Post by manfer on 2008-06-29
> **vanflyheight13 said:**
> [ftp://86.15.20.93/](ftp://86.15.20.93/) is the way I'm trying to access it.

[ftp://localhost/](ftp://localhost/) works absolutely fine and shows all my files, but when I try to access it through the [ftp://IP](ftp://IP) / method I just get an page with no files.

If it not accessible from outside you could think of something blocking the access. That's the router permits access to ftp port? Do you have any firewall enable?

---

### Post by manfer on 2008-06-29
Not the problem. You say you can enter but you see it with no files.

Pressing the button to go up the files would be there. I don't know exactly why, not very familiarized with ftp. I don't use it too much.

I would try to config anon_root on the config file and I tell if it works.

---

### Post by untermensch on 2008-06-29
There should be a dir to which you put all your ftp server info.. and you can put it in there, but I found that I can search threw my whole computer. Did you edit your configuration files properly?

O also, try opening a terminal and just typing ftp <servers'sip>, then you'll have to put in the username and password (if you set them up) and you should be able to see them from there. you can download the files you want by moving to that directory and typing get <filename> without the < > 's

---

### Post by manfer on 2008-06-29
I would look tomorrow for the problem. Trying to access from an ftp client reports an error when trying to get the directory listing.

---

### Post by manfer on 2008-06-30
In firefox try:

[ftp://anonymous@your_ip/](ftp://anonymous@your_ip/)

it looks like firefox needs the user and password if needed to be specified.

Try to connect with a ftp client too.

If it is not working that way, then the problem is with router configuration.

---

### Post by vanflyheight13 on 2008-06-30
Thanks for the help guys, but I think I'll just cut my losses on this one. :(

The speed of response from you guys was amazing!

---

