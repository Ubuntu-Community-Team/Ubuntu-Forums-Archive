---
title: "How does home folder encryption work ?"
date: 2013-04-02
forum: General Help
---

### Post by MickeyPilgrim on 2013-04-02
I put 12,04 on my desktop and checked the box for encryping the home folder. 

Nothing seems to be encrypted. I copied a file to a thumb drive and tried it on another computer and it opened right up. Where do I learn how to apply encryption?

---

### Post by Frogs Hair on 2013-04-02
If you selected the option during installation I don't know what may have happed.  If after installation this might point in the right direction. [http://www.howtogeek.com/116032/how-to-encrypt-your-home-folder-after-installing-ubuntu/](http://www.howtogeek.com/116032/how-to-encrypt-your-home-folder-after-installing-ubuntu/)

---

### Post by Paqman on 2013-04-02
> **MickeyPilgrim said:**
> 
Nothing seems to be encrypted. I copied a file to a thumb drive and tried it on another computer and it opened right up. Where do I learn how to apply encryption?

That's normal. Your home folder will only be encrypted when you're not logged in. When you log in and open the files in your home folder they're decrypted. The idea behind home folder encryption is that anybody who's not you (ie: is not logged in as you) sees only encrypted data. To you everything looks just the same as it would without home folder encryption.

If you want files transferred to an external medium to be encrypted then you'll have to encrypt them yourself.

---

### Post by MickeyPilgrim on 2013-04-04
Thanks for that, but is there a way to know that for certain?

---

### Post by sudodus on 2013-04-04
Yes. Boot from your ubuntu install CD/DCD/USB drive, mount the root or home partition and check your home directory, something like

/home/mickey

Now you should see only a README file and some encrypted files (or links to encrypted files).

---

### Post by MickeyPilgrim on 2013-04-05
Thanks.
Where is the "Solved" button?

Mickey

---

### Post by sudodus on 2013-04-05
You are welcome :-)

There is a workaround. See this link[COLOR=#ff0000]

[/COLOR][[COLOR=#ff0000]http://ubuntuforums.org/showthread.php?t=2121377[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2121377")

---

### Post by MickeyPilgrim on 2013-04-05
Suddos,
  The home folder encryption is so quick and easy. I'm wondering if you know , or would recommend a fast encryption technique for the legal files I need to put on back-up.
 They don't require the highest level of crypto, just a decent way of keeping them from being obvious.

Mickey

---

### Post by Nr90 on 2013-04-05
GnuPG is AFAIK the standard when it comes to encrypting pretty much anything :)

---

### Post by Raveni on 2013-07-04
Hi
I have couple of question with home folder encryption... Can I change login password? and how I have to do it... I don't want problems with encryption. Can I change computer name without problem if I use encryption?

---

### Post by sudodus on 2013-07-04
No, I think you should select password with care (a good one, that you can remember, and that people or machines cannot find easily). It might be possible to change password, but I don't know how (and I have encrypted home myself in one system). And there might be work-arounds: that you backup your home directory while logged in (so that the files are saved unencrypted). Then you restore an unencrypted system and you might be able to encrypt it. But the unencrypted data will remain on the drive space and must be wiped ... It gets complicated and maybe not very secure.

I don't think the computer name is involved in the encryption, only the user name and user password and a special pass-phrase. So I think you can change the computer name (but I have not tried it).

---

### Post by Raveni on 2013-07-06
Thank you for answer... So if I change account password I could get trouble with encryption...

---

