---
title: "webmin Error - Access denied for ipadress"
date: 2005-10-31
forum: General Help
---

### Post by irv on 2005-10-31
After I typed the command sudo apt-get install webmin at the server, (which went well) (Which installed Webmin), I go to the desktop and in my browser I typed: [http://192.168.0.100:10000](http://192.168.0.100:10000) and nothing happens. So I tried [https://192.168.0.100:10000](https://192.168.0.100:10000) and I get an Error - Access denied for 192.168.0.102 which is my desktop. Do I have to set permisions on my destop or on the server? And where do I go and what do I do?

---

### Post by suRoot on 2005-11-01
Try [http://127.0.0.1:10000](http://127.0.0.1:10000)

---

### Post by irv on 2005-11-11
Instead of making a new post, I thought I would ask the same question I did in Oct. I have not got webmin to work yet. When I enter https or [http://server-ip:10000](http://server-ip:10000) I still get "Access denied for ipaddress". I tried this from the workstation and the server. 
Does webmin run as a server? After installing it on the server do I have to do something to start it?

---

### Post by cedjo on 2005-11-11
You could try to tune the line "allow=" in /etc/webmin/miniserv.conf and then restart webmin with /etc/init.d/webmin restart **as root**

---

### Post by irv on 2005-11-11
This worked great. the Allow line in miniserv.conf was 127.0.0.1 and I changed it to 192.168.0.0. and I now get the login screen.
I do have one more problem. Now that I get the login, it will not let me login either as root or myself. I don't remember setting a password for webmin. Do you know what it is? or where can I change it?
Thanks again.

---

### Post by cedjo on 2005-11-11
for your passwd problem you should have a look [here]("http://ubuntuforums.org/showthread.php?p=16865")

---

### Post by irv on 2005-11-11
In the link you sent me to it said:
--------------------------------------------------
In /usr/share/webmin/ there is a Perl script called changepass.pl to change root password in webmin use this:

# /usr/share/webmin/changepass.pl /etc/webmin root <your passwordhere>

And that will fix it! No install/removal necessary.
--------------------------------------------------
I am not sure how to do this. If I type 
sudo /usr/share/webmin/changepass.pl /etc/webmin root <password> I get an error. Just looking at what I typed I see I left of the # sign. When I get home from work I will try that. Maybe that is what I did wrong.

---

### Post by irv on 2005-11-11
Well, I got home from work and try it, didn't get any errors, but it is not changing the password.
Is there a file I can edit to manually change the password, or do I have to uninstall and reinstall webmin and reset everythig up again? I sure how not?

---

### Post by irv on 2005-11-12
Thought I would give a final update on all I did to get webmin going.
 I did go to the the link  and type in # /usr/share/webmin/changepass.pl /etc/webmin root <my new password>, but this did not work. I tried it many times. Final I uninstall all and reinstall. While I was installing it this time I took note when the message box came up and said; 

The webmin system uses a separate password file /etc/webmin/miniserv.users

An initial version of this password file has been generated for you. It contains only a 'root' user, with the password copied from the password file.

This was great but I never set a password when I installed Ubuntu so I still had now idea what the password was, so I was back to square one. Reinstalled again, but this time I went and set my root password first, and then I was able to get webmin to work. I wasn't real happy with it though because many of the mod's would not work right.
I used webmin on a Susi Linux box and everything work the first time around. I did download it from the IBM site as I remember. 
Well, now you have the whole story.
Hope this might help someone down the road.  Happy Ubuntuing.
 [QUOTE=irv]There are many nerves in the human body, but the most sensitive is the one that goes from the brain to the pocketbook. :D [/QUOTE]

---

### Post by koka on 2005-11-15
sounds like webmin is not running. In a terminal window as superuser try,
/etc/webmin/start

---

### Post by engine on 2005-11-25
cedjo - thanks both to you and to hendrcks! It's all easy when you know how, but finding out how in the first place ...

---

### Post by talz13 on 2005-12-22
[QUOTE=irv]This worked great. the Allow line in miniserv.conf was 127.0.0.1 and I changed it to 192.168.0.0. and I now get the login screen.
I do have one more problem. Now that I get the login, it will not let me login either as root or myself. I don't remember setting a password for webmin. Do you know what it is? or where can I change it?
Thanks again.[/QUOTE]

I've been getting this error now.  I checked the miniserv.conf and changed the allow line from 

allow=127.0.0.1

to each of these and still get the access denied error:
allow=192.168.1.*
or
allow=192.168.1.0
or
allow=192.168.0.0


(restarting between changes, of course)

---

