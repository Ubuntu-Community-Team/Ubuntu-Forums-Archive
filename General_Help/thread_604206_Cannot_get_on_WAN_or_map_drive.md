---
title: "Cannot get on WAN or map drive"
date: 2007-11-05
forum: General Help
---

### Post by onetwoalpha on 2007-11-05
_Disclaimers_:

I am new to Linux altogether.

I am running the following:
[LIST]
[*]Ubuntu 6.06 LTS Server Edition (LAMP) (with GUI)
[*]Webmin 1.370
[*]Linksys Wireless Router WRT54Gv6
[/LIST]


Since I am new to Linux I am hoping someone smarter than me can give some help. Here is what I am hoping for and what my issue(s) are:

I run the Linux PC as the testing server and a development PC running Windows XP Pro SP2. I can view the parent directory of '_/var/www_' by entering in my LAN IP Address '_192.168.1.xxx_' in my browser. I would like it to auto load my '_index.htm_' page but for some reason it will not. I have a feeling it has to be '_.html_' or '_.php_', but would like some confirmation.

I am also trying to map that directory of '_/var/www_' so I can connect to it using Macromedia (Adobe) Dreamweaver via my development PC.

If possible I would like to get my web sites to show on a WAN as well. I am not looking to host the sites for regular usage, but I would like to have remote access to my sites that are in development so family/friends can check them out every so often, etc.

I setup port forwarding but I am confused as to the difference(s) between port '_80_' and '_8080_'. I know my ISP doesn't block it though.

I hope I am making sense and giving the appropriate information.

I have been dedicating all of my off time over the past week to Google-ing myself to the point I am now. I am giving in and asking others hoping someone can give me an answer or some guidance.

Essentially;

**1.** Need to setup auto loading of index.htm page in root directory.
**2.** I need to map to the Linux PC from Windows PC.
**3.** Get sites to work on the WAN.

Please advise. I greatly appreciate any and all feedback you can give me.

---

### Post by mpierce on 2007-11-05
If you want to setup your WAN so that your XP box can connect to it, you need to setup Samba on your linux box and then you will be able to map the drives under XP.

Install, samba and samba-common.
   sudo apt-get install samba-common, samba

You need to configure, /etc/smb.config to grant access by editing the file. If you need a copy of mine, it has been posted before so search for it. Make sure the WORKGROUP is identical on all boxes. 

Restart samba:
   sudo /etc/init.d/samba restart

You'll also need to set the properties to share for the drives/directories that you want to see from your linux box that are on the XP box. From your linux box you can quickly check if they are functional by using konqueror's plugins, e.g.
   smb://192.168.1.252/mpierce

This shows me all the files on my XP notebook as this is the My Documents shared folder. 

Hope this helps... Others know the track from here so anyone can help you!

---

### Post by onetwoalpha on 2007-11-05
Ok scratch the '_.htm_' file extension issue, I found the command to change the file name to '_.html_' and it works as suspected. I still can't figure out the other issues though.

Again any feedback is greatly appreciated.

---

