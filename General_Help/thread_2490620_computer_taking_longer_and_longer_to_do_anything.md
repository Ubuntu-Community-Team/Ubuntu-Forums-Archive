---
title: "computer taking longer and longer to do anything"
date: 2023-09-09
forum: General Help
---

### Post by jgw on 2023-09-09
My computer is getting slower and slower.  When starting up, for instance, it shows the background, etc. and then takes a bit more than 5 minutes to finish opening.  I now find that when I think that the system is frozen its just taking its time.  I have had it freeze and then, a half hour later, opens a file I wanted to look at.  If I want to run files to see something that might take between 5 and 15 minutes.  Stuff like that.  I installed hardinfo so I could send something on my machine.  Took over 20 minutes and the report is rejected by ubuntu even though I copied the text and put it into a text file.  I also have system-info but forget how I used it.  I tried to install something called screenfetch and neofetch but ubuntu couldn't find them. 

I pasted the hardinfo report at [https://paste.kodi.tv/ewelesavik](https://paste.kodi.tv/ewelesavik)

If anybody can send me something to run to show my system I would appreciate it.  Then I would have something to show anybody who might be interested.  

Thoughts?

---

### Post by TheFu on 2023-09-09
Check that DNS is working.  There are a surprising number of things that get really slow with a malfunctioning DNS.

Also, check the system logs.  I've never looked at hardinfo before.  Seems like it lists every CPU possible.  I'd rather see **inxi -Fzxx**  or the sys-info script output from [https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info). The 2nd is designed to gather information for troubleshooting.  But at some point, looking at the system logs is mandatory.

---

### Post by MAFoElffen on 2023-09-09
Forgot how to use the [system-info script]("https://github.com/UbuntuForums/system-info")?

If you downloaded the script from the Github, then change directory to the folder you downloaded it to, then do
```

./system-info

```
If you added the PPA and installed it as a program, then do
```

system-info

```
Follow the online prompts, then choose to upload it to a pastebin. Copy the displayed URL of the upload and paste that URL into your post.

I tried to make it easy to use, and have many prompts to help guide the User through using it. Feel free if you have any comments or questions.

Additional to the report... Is everything running slow? or Just while browsing? It sounds like everything may be... And taking so long to boot... Maybe what might help in this case is posting the result sof
```

sudo systemd-analyze blame

```
Remember to post that output "within Code Tags". If you do not know how to do that, please ask for instructions.

@TheFU --- Remember? "sys-info" was name TheFu had personally suggested to me that that I named the script that... I instead made it more descriptive. Thank you all. I hope that it helps many users, and Members for years beyond me.

---

### Post by jgw on 2023-09-09
Thank you for the replies.

Here is the result of the first one:
```
greg@greg-desktop:~$ wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && \
chmod +x system-info && \
./system-info
--2023-09-09 16:00:01--  https://github.com/UbuntuForums/system-info/raw/main/system-info
Resolving github.com (github.com)... 192.30.255.113
Connecting to github.com (github.com)|192.30.255.113|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://raw.githubusercontent.com/UbuntuForums/system-info/main/system-info [following]
--2023-09-09 16:00:01--  https://raw.githubusercontent.com/UbuntuForums/system-info/main/system-info
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.108.133, 185.199.111.133, 185.199.110.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.108.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 87553 (86K) [text/plain]
system-info: Read-only file system

Cannot write to &#8216;system-info&#8217; (Success).
```


The second one is different.  Its the complete thing but my system won't let me save it and I will keep on trying but I want to get this off before I lose it.

I found a little useless file.  I deleted what was in it and dumped it all into that file.  The file is named subaru and my system refuses letting me change the name (greyed out)  I own it so I don't get it but its this machine!

So, I have it downloaded.  It was where the second sent me.  This is where I ended up:
[https://raw.githubusercontent.com/UbuntuForums/system-info/main/system-info](https://raw.githubusercontent.com/UbuntuForums/system-info/main/system-info) 

I am going to shut this system down and then restart it.  If I try and just reboot it won't work.  

Thoughts?

---

### Post by ian-weisser on 2023-09-09
Your output seems clear enough:

```
system-info: Read-only file system
```

Patiently peel back the next layer of the onion.

---

### Post by jgw on 2023-09-09
I was going to add to my last.  I was told that I didn't have the right to do that (I am logged in!)  Anyway, I was able to change the name of the file to system-info.  Now what do I do with it?  Oh, where are my system logs.  If I can find them I will post at least one of them.  Just checked the system logs at /var/log the last one posted there was was Monday!!  Suspect that might not help.

What do you want me to do with the system-info thing that I now have.  Should also tell you that I have used that about 3 times but forgot how - getting old and memory stinks.

---

### Post by jgw on 2023-09-09
I lost system-info as the system changed it to 2 lines of nothing

I the the sudo systemd-analyze blame and got :

```
greg@greg-desktop:~$ sudo systemd-analyze blame
[sudo] password for greg: 
7min 40.926s systemd-tmpfiles-clean.service
 2min 5.603s update-notifier-download.service
     44.014s plymouth-quit-wait.service
     41.134s apt-daily-upgrade.service
     10.329s gpu-manager.service
      5.058s NetworkManager-wait-online.service
      2.934s setvtrgb.service
      2.302s fwupd.service
      1.838s snapd.service
      1.189s e2scrub_reap.service
       977ms networkd-dispatcher.service
       730ms dev-loop20.device
       726ms udisks2.service
       722ms cups.service
       718ms dev-loop17.device
       707ms dev-loop8.device
       703ms dev-loop12.device
       690ms dev-loop6.device
       689ms dev-loop16.device
       688ms snapd.seeded.service
       686ms dev-loop11.device
       685ms dev-loop10.device
       673ms dev-loop5.device
lines 1-23

```

---

### Post by jgw on 2023-09-09
I actually went back and got a new copy of the script and named it system-info

greg@greg-desktop:~/Documents$ ls
system-info
greg@greg-desktop:~/Documents$ ./system-info
bash: ./system-info: Permission denied

I own system-info but I can't run it.  I think I read not to use sudo with it.

---

### Post by MAFoElffen on 2023-09-09
You have to change the permissions on it to execute it as a script first. To do that, do this
```

sudo chmod +x ./system-info
./system-info

```
This result here:
```

7min 40.926s systemd-tmpfiles-clean.service

```
Indicates that you are having problems with a corrupted filesystem and should correct that. The easiest way to do that would be to reboot ad get to the Grub2 Menu. At the Grub2 boot menu, Select Advanced Options. Then select a boot option with Recovery. At the Recovery Menu, select fsck. That will run that on the file system mount lines setup in your fstab file and correct them...

Tell me how that goes.

---

### Post by TheFu on 2023-09-09
Whoa there.   He has a read-only file system.  That means the partition he's on has some issues, unless he did something really odd.  

Let's back up a bit.
Slow system.
Read only file system.
That says that the system is crippled in some way. Could just be a corrupt file system, but it could also be a dying HDD/SSD.  Needs to look at the system logs to figure it out.

---

### Post by MAFoElffen on 2023-09-09
That's what I said in Post #9. Note his output from "system-analyze blame"... Shows almost 8 minutes during boot up trying to work out filesystem issues.

---

### Post by jgw on 2023-09-10
Thank you for all the help!

I have to fill you in on some stuff.  First, I am using 1tb ssd's for booting.  I am currently seriously thinking of just reformatting and installing a new ubuntu on it.  Last night I turned off the system - it refused to shut down.  When this happens its time for something else.  I think I may need a new system.  This one is pretty old.  I have found that when you want to buy a computer, with no system and no hdd's you can get one for a pretty good price on ebay.  This morning I tried to open this one and it doesn't want to startt either.  This system is used for one thing, it plays downloaded videos for us at night - that's it.  This means that it actually has, maybe, 4 programs and that too is it.  All my data is on a couple of 4tb hard drives, one for the videos and one to backup the videos.  That's pretty much it.  

I now have it downstairs in my hole - this is, pretty much, what I do when my wife doesn't drag me off to foreign climes.  

I am going to try the recovery thing that was suggested to see what happens.  If it continues, however, I am going to take a ssd, put a new ubuntu on it and then just have at it.  I have also noticed that ssd's are actually not exactly always there but that is what gparted is for.  They sometimes go bad but, apparently, they don't get seriously wrecked and they tend to be able to get cleaned up and re-constituted. 

Anyway, I appreciate all the efforts and I will let you know what happens.

---

### Post by jgw on 2023-09-10
Thank you for all the help!

I have to fill you in on some stuff.  First, I am using 1tb ssd's for booting.  I am currently seriously thinking of just reformatting and installing a new ubuntu on it.  Last night I turned off the system - it refused to shut down.  When this happens its time for something else.  I think I may need a new system.  This one is pretty old.  I have found that when you want to buy a computer, with no system and no hdd's you can get one for a pretty good price on ebay.  

This morning I tried to open this one and it doesn't want to start either.  This system is used for one thing, it plays downloaded videos for us at night - that's it.  This means that it actually has, maybe, 4 programs and that too is it.  All my data is on a couple of 4tb hard drives, one for the videos and one to backup the videos.  That's pretty much it.

---

### Post by jgw on 2023-09-10
I made another run at system-info and got after sudo chmod +x ./system-info:

This script needs some parts of it to run with elevated permissions.

Please enter your password for that to happen.
[sudo] password for greg: I stopped

that system-info I got around 24 september 2022  guess I should get the newer one?:

---

### Post by MAFoElffen on 2023-09-10
If you did
```

./system-info -v

```
That would return the version and script date. 

This is what is current:
```

version="Version: 02.00-08, Script Date: 2023.05.24"

```
I think there was only a minor change in there, Between your date and then... And that had to do about features I added for file systems and file managers when using the "--details" start up option.

---

### Post by #&amp;thj^% on 2023-09-10
> **MAFoElffen said:**
> 
This is what is current:
```

version="Version: 02.00-08, Script Date: 2023.05.24"

```
I think there was only a minor change in there, Between your date and then... And that had to do about features I added for file systems and file managers when using the "--details" start up option.
+1 This is today.
```
Version: 02.00-08, Script Date: 2023.05.24
```

---

### Post by MAFoElffen on 2023-09-10
You didn't say or mention it... 

Did you go to the "Rescue Menu" and do 'fsck' yet? And what did it find and repair?

---

### Post by jgw on 2023-09-11
Version: 02.00-08, Script Date: 2023.05.24

tried this:
```
sudo chmod +x ./system-info
./system-info
This script needs some parts of it to run with elevated permissions.

Please enter your password for that to happen.
[sudo] password for greg: 

```

This is on my good machine (so far) Something odd going on I fear.  I think I will try to get another copy and try again.  

I have decided to give up on the other machine.  Too much wrong to fix and some, I think, is hardware.  I use Private Internet Access (PIA) for my vpn.  Supposed to be a good one and I know of at least a couple that are free.  Anyway, that system would not let PIA connect.  (they are fixing it, I think but don't really care.  That was interesting as I also have a display in the top bar which tells me about what is going on with graphs.  One of those is 'network' and its always been going full blast even when I am doing nothing.  PIA as has an option to stop ALL internet which I turned on.  Now that machine keeps trying and failing to do whatever it was doing so things are not all bad.  I replaced the boot ssd with a new one with nothing but ubuntu on it and it continued with boots that didn't or took all day, etc.  It also still didn't like to shut down and had to be turned off.  There was other strange stuff as well.  It was time to replace (have another in a week or so).  

I thought to take a look at the code for system-info and found that the stuff above come from that one. I wonder if I was supposed to run sudo.
```
  echo -e "This script needs some parts of it to run with elevated permissions."
        nl
        ## Check if 'sudo' is installed...
        if type sudo > /dev/null 2> /dev/null
        then
           echo -e "Please enter your password for that to happen."
           sudo -k # revoke previously cached sudo password 
            if sudo true
            then 
                echo -e "Running Script: ${sname} $version"
            else 
                echo -e "$redback ----------- This script is made to use 'sudo' ----------- $resetvid"
                echo -e "$redback ---- Password was incorrect for sudo elevated rights. --- $resetvid"
                PassPhrase
                echo -e "Continuing to run the script, but: Expect errors. "
            fi
```



I want to thank you for all the help.  At least we tried which is not all bad.

---

### Post by MAFoElffen on 2023-09-11
No. 

It is meant run without sudo, because some commands used in the script *need to run as the User* (to gather the User information) but will ask for your password, to use 'sudo' elevated permissions where and when it needs to. It will only ask for that once.

I am still waiting for the results of you running 'fsck' from the Rescue Menu. That is a utility that is mean to check and repair the ext4 filesystem. I'm sorry, but I'm going to latch onto that like a pit bull... As that is what your output so far says is going on... 

If you ran the 'system-info', even in it's oldest form, then one of us could use info from that to give you the exact command to run, on the filesystem you need, to. But without that information from you, I am not clairvoyant.

We 'are trying to help you. Though you seem to be unwilling to follow the given directions and to answer, what seems to me, as simple questions, to provide information. If you continue this path, and do not follow what we recommend or ask for, then I will assume that you do not want to try to fix your computer and I will go on to help someone who does want help.

---

### Post by dazz411 on 2023-09-12
It could be a hard drive failure. Check health of the Hard Drive with HDD Sentinel.

---

### Post by jgw on 2023-09-24
I forgot to make this solved.  What I did was simply replace the boot ssd with another and, suddenly, everything was working again and all I had to do was re-install some stuff.

thank you all for the help.

---

### Post by MAFoElffen on 2023-09-24
You are welcome. Glad that things are working well for you again.

---

