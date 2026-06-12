---
title: "Downloaded wine - now what?"
date: 2006-12-22
forum: General Help
---

### Post by atarileaf on 2006-12-22
Hello. I followed the instructions on this page:

[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

So I was able to download it but now I can't find the program in my Applications or anywhere else it seems. Where did the download go? I need to find the installer to install the thing and I'd like a wine icon on my desktop. Can anyone help me please?

Thanks

---

### Post by iamhugeinjapan on 2006-12-22
Go Alt+F2 and run winecfg this will spawn a /.wine/ folder in your Home directory that will house a virtual C:\  (/.wine/drive_c/)

Close it then then find an executable you want to run with nautilus, right click and choose Open with...  put Wine in the custom command.

If you're lucky the program will come up.

It's often best to trouble shoot a program by opening it from a console first.  'wine' then the path to the executable. example:

```
 wine /mnt/windows/windows/notepad.exe
```

That way you see any error messages about missing files etc.

When you have a program working you can create a launcher icon in the usual way but put  wine + path in the command field.

---

### Post by maxamillion on 2006-12-22
When you say "download" did you actually download a package .deb file or use apt-get, aptitude, or synaptic to install it?

If you installed it, then you need to run the command "wine" in a Terminal.

---

### Post by aysiu on 2006-12-22
I think you should read this page:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

and then this one:
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

### Post by atarileaf on 2006-12-22
I used synaptic. I think I've got it. I ran windows cd and installed it. It seems to work. One question. Where does wine (or Ubuntu) put the programs I installed? I don't see a /wine directory when I search the computer and go to file system. I'd like to put an icon for the windows program on the ubuntu desktop so it runs automatically.

Thanks for your help and patience everyone! :D

---

### Post by aysiu on 2006-12-22
The Wine directory is hidden.

If you go to /home/atarileaf and then press Control-H (or Alt-V, H in Kubuntu), you'll see a bunch of hidden directories.

One should be called .wine

---

### Post by FLPCGuy on 2006-12-22
[iamhugeinjapan]("http://ubuntuforums.org/member.php?u=129529") That was a great short explanation of wine!  I'd love to see more explanations like this for other features new users must learn about.

---

### Post by iamhugeinjapan on 2006-12-23
Thank you, I hope it helped.

---

