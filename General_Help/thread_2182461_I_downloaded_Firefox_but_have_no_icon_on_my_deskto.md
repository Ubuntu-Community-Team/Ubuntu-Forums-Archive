---
title: "I downloaded Firefox but have no icon on my desktop"
date: 2013-10-21
forum: General Help
---

### Post by Kate_Austin on 2013-10-21
I wonder if someone can help me please.. I have been running Ubuntu for just over a year but when i upgraded to version 13.04 my ISP crashed causing me to lose everything . i managed to reinstall it and install firefox but i have no icon for firefox on my desktop . Also i am trying to set up Firefox profile manager but am having problems with this also . Any advice or help would be greatly appreciated . Thank you

---

### Post by vanadium on 2013-10-21
Are you using Ubuntu? Ubuntu does standard come with firefox preinstalled.

---

### Post by Kate_Austin on 2013-10-21
Yes i am using it . i had to install FF as when i clicked on web browser it told me i had to install a browser to enable me to get online. so i installed FF and its telling me i have the latest version of it . Im so confused :/

---

### Post by Bucky Ball on 2013-10-21
Welcome. Are you saying your ISP crashed, thus your internet connection died, part way through an online upgrade (by clicking the icon in Update Manager and going from 12.10>13.04)? If so, that is not good. 

What happens when you run the regular update manager? Could you please post any error messages you get when you try a regular update? If nothing, and/or also, run these commands in a terminal one after the other, pressing return in between:

```
sudo apt-get update
sudo apt-get upgrade
```

Post any error messages you get, particularly after the 'upgrade' command.

---

### Post by Kate_Austin on 2013-10-21
Yes im afraid that is what happened.. i did manage to bring my pc back from the dead and since writing this have managed to launch Firefox and now have it as an icon .. i am however having problems with the FF profile manager as it will only open one account at a time and that one has to be shut down before i can open another one. im sure i have to enter a   no remote command but obviously not entering it properly . I will do as you say and see what error messages if any i get . thank you

---

### Post by Bucky Ball on 2013-10-21
All I can say for the moment is have you got your personal stuff backed up? It might not come to that but might be an idea to boot from the LiveCD and backup what you need to somewhere if you haven't already got it safe (unless your system is stable enough to do it while running from the install, but might be better from a CD).

This is presuming your personal data is not backed up and resides in a /home partition inside / and not on a separate /home partition or different physical drive to / . ;)

---

### Post by Kate_Austin on 2013-10-21
wow im not sure what happened but i done as you said and it scanned lots of stuff.. i had nothing backed up as i just use this pc for gaming .. when i crashed i  done it properly . my hard drive went also but thanks to a geek friend of mine he talked me through how to get my pc back on skype .. i managed to do this and also burnt off an Xubuntu 12.10 disc using my laptop and loaded that . then i had a pop up again telling me that i had 290 updates so i updated and hence have now got Ubuntu 13.04. this is just some of what just came up in the terminal after i typed in what you said lol.. Im blonde and stryuggling here so please be patient with me lol ... Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/universe Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/main Translation-en_GB         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/multiverse Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/restricted Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/universe Translation-en_GB     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/main Translation-en_GB       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/multiverse Translation-en_GB 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/restricted Translation-en_GB 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/universe Translation-en_GB   
Fetched 890 kB in 6s (132 kB/s)

---

### Post by Kate_Austin on 2013-10-21
Then this came up .. (process:3068): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed

---

### Post by Bucky Ball on 2013-10-21
Sorry, can you run the commands and copy/paste their output back to a post if there is an error? Thanks. ;)

I presume you can run 'sudo apt-get update' without problems? How about the other?

But yea, looks like you made it to 13.04.

---

### Post by Kate_Austin on 2013-10-21
You want me to post all the commands in here???

---

### Post by Kate_Austin on 2013-10-21
nne@anne-MS-7788:~$ sudo apt-get upgrade
[sudo] password for anne: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Bucky Ball on 2013-10-21
Re-read my last post. Edited.

But just tell me. 'sudo apt-get update' produces no errors (I'm presuming)? 'sudo apt-get upgrade' gives:

 '(process:3068): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed' 

But yea, you can just copy/paste the output from the terminal directly into a post easiest and can see where the errors are occurring. ;)

---

### Post by Kate_Austin on 2013-10-21
anne@anne-MS-7788:~$ sudo apt-get update
[sudo] password for anne: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring Release.gpg
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg [72 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release                        
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates Release.gpg [933 B] 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Sources                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Sources                               
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates Release [40.8 kB]  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Sources            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main amd64 Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Sources                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main amd64 Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/main Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/main amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/restricted amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/universe amd64 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/multiverse amd64 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/universe Translation-en
Get:4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/main Sources [76.5 kB]
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/restricted Sources [14 B]
Get:6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/universe Sources [73.1 kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en_GB
Get:7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/multiverse Sources [2,266 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en_GB
Get:8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/main amd64 Packages [194 kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en_GB
Get:9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/restricted amd64 Packages [14 B]
Get:10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/universe amd64 Packages [151 kB]
Get:11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/multiverse amd64 Packages [3,715 B]
Get:12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/main i386 Packages [192 kB]
Get:13 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/restricted i386 Packages [14 B]
Get:14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/universe i386 Packages [152 kB]
Get:15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/multiverse i386 Packages [3,864 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/main amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/restricted amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/universe amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/multiverse amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/universe Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/main Translation-en_GB         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/multiverse Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/restricted Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/universe Translation-en_GB     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/main Translation-en_GB       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/multiverse Translation-en_GB 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/restricted Translation-en_GB 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/universe Translation-en_GB   
Fetched 890 kB in 6s (132 kB/s)                                                
Reading package lists... Done

---

### Post by Bucky Ball on 2013-10-21
Well, that's fine. And immediately after that run the 'sudo apt-get upgrade' command. Error?

---

### Post by Kate_Austin on 2013-10-22
No i didnt get the error when i ran the upgrade command . that  popped up in another terminal .. im trying to install FF profile manager and i think it has something to do with that ? i can only run one account at a time . i think i have to add a command like this ~~> \Mozilla Firefox\firefox.exe" -P -no-remote    .. but its not recognising it :/ any chance you can pop round and fix all this for me ? lol

---

### Post by Kate_Austin on 2013-10-22
when i open up profile manager i get this ~> (process:1922): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed

---

### Post by Bucky Ball on 2013-10-22
> **Kate_Austin said:**
> ... any chance you can pop round and fix all this for me ? lol

Not unless you live in Australia and even then no guarantees, because ...
 
Can I assume the original problem of not having a Firefox icon on the desktop is solved and now you have a problem with Firefox profile?

Can't really help with that. Don't know anything about the Firefox profile manager, sorry. If your original problem is solved, though, it might pay to mark this thread as solved and start a new one with a title befitting your new issue, as this one has nothing to do with it. Might have more luck that way.

;)

---

### Post by Kate_Austin on 2013-10-22
Yes you are correct . i will do that thank you  for your help /patience and time :)

---

### Post by Bucky Ball on 2013-10-22
All good and no probs. 

Good luck with it and see you around the forums. ;)

---

