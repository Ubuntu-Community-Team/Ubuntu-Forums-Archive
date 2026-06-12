---
title: "Samaba can not read Vista shared folders"
date: 2007-02-01
forum: General Help
---

### Post by jae1227 on 2007-02-01
I just installed vista yesterday. I thought it was great!. The look and feel was great. Then I wanted to watch a movie on XBMC. So I want to the network area on XBMC and clicked on my vista computer's shared folder. I waited and nothing happened. So I thought I would try my Ubunut box. I went to my vista box on Ubuntu and clicked on the shared folder. This time it prompted me for a user name, domain, and password even thou it is a shared folder without a password. So I went to my other XP computer and guess what, it worked fine. In XP it saw the shared folder like any other shared folder. Now before vista came out I heard Microsoft told its employees to "F*** with samba". I wonder if this problem I am having is from MS or if I just need to change something in the control panel.
So I think the easiest thing to do is to change something is vista to make it be like how it was in XP but that might not be possible. Does anyone know any fixes?

---

### Post by droogie2799 on 2007-02-01
I am by no means an expert but the problem you are having was similiar to one I was having so I thought I would chime in.  Here is what I did to fix the issue.

```
gksudo gedit /etc/samba/smb.conf 
```

Find these lines


```
# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
# in the samba-doc package for details.
;   security = user
```

Change the last line to:

```
security = share
```

for more information see this 

For more info see [http://easylinux.info/wiki/Ubuntu_Edgy#Samba_Server](http://easylinux.info/wiki/Ubuntu_Edgy#Samba_Server)

I am actually installing Vista as I type this so I will see how it goes.

---

### Post by droogie2799 on 2007-02-01
Just wanted to update anyone else trying the same.  I was able to access my Ubuntu shares from my Vista box.  I installed Vista Business.

---

### Post by jae1227 on 2007-02-01
> **jae1227 said:**
> I just installed vista yesterday. I thought it was great!. The look and feel was great. Then I wanted to watch a movie on XBMC. So I want to the network area on XBMC and clicked on my vista computer's shared folder. I waited and nothing happened. So I thought I would try my Ubunut box. I went to my vista box on Ubuntu and clicked on the shared folder. This time it prompted me for a user name, domain, and password even thou it is a shared folder without a password. So I went to my other XP computer and guess what, it worked fine. In XP it saw the shared folder like any other shared folder. Now before vista came out I heard Microsoft told its employees to "F*** with samba". I wonder if this problem I am having is from MS or if I just need to change something in the control panel.
So I think the easiest thing to do is to change something is vista to make it be like how it was in XP but that might not be possible. Does anyone know any fixes?

Yeah I had no problems with that. I can not get Linux or my XBOX running samba to read from my vista box. The vista box is fine and can access anything but only other windows computers can talk to vista. So samba devices can not view files on vista's shared folders.

---

### Post by tminuszero on 2007-02-07
> **jae1227 said:**
> So samba devices can not view files on vista's shared folders.

Actually, I think it's actually that *Linux* samba devices cannot view files on Vista computers.  Macs run samba, and have few problems. They only need to set this in the global settings of smb.conf:

client ntlmv2 auth = yes
client lanman auth = no

At least that's what I've heard. The second line is kinda unnecessary.

Here's a PDF article of the problem in Linux Magazine:

[http://www.linux-magazine.com/issue/75/Microsoft_Vista_With_Linux_Interoperability.pdf](http://www.linux-magazine.com/issue/75/Microsoft_Vista_With_Linux_Interoperability.pdf)

I don't know about your Xbox issue, but I'm assuming you're running linux.

---

