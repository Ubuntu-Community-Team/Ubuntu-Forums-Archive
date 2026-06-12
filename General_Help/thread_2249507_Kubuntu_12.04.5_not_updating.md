---
title: "Kubuntu 12.04.5 not updating"
date: 2014-10-22
forum: General Help
---

### Post by Al1000 on 2014-10-22
Hi,

I received a system notification this morning saying that updates were available, but Muon Update Manager wouldn't download them. I tried again this evening, and am getting the same error message as follows:

 > Failed to download [http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources) 404 Not Found [IP: 91.189.92.200 80] Failed to download [http://gb.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages) 404 Not Found [IP: 91.189.92.200 80] Failed to download [http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages) 404 Not Found [IP: 91.189.92.200 80] Failed to download [http://gb.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages) 404 Not Found [IP: 91.189.92.200 80] 

I also tried updating through the terminal, and the same happens there too.

```
al@my_laptop:~$ sudo apt-get update
Hit http://extras.ubuntu.com precise Release.gpg
Hit http://ppa.launchpad.net precise Release.gpg                                             
Hit http://extras.ubuntu.com precise Release                                                 
Hit http://gb.archive.ubuntu.com precise Release.gpg                 
Hit http://gb.archive.ubuntu.com precise-updates Release.gpg         
Hit http://gb.archive.ubuntu.com precise-backports Release.gpg       
Hit http://security.ubuntu.com precise-security Release.gpg          
Hit http://ppa.launchpad.net precise Release                         
Hit http://security.ubuntu.com precise-security Release              
Hit http://gb.archive.ubuntu.com precise Release
Hit http://gb.archive.ubuntu.com precise-updates Release
Hit http://gb.archive.ubuntu.com precise-backports Release
Hit http://extras.ubuntu.com precise/main Sources
Hit http://extras.ubuntu.com precise/main i386 Packages                                 
Ign http://extras.ubuntu.com precise/main TranslationIndex                              
Hit http://ppa.launchpad.net precise/main Sources                                       
Hit http://ppa.launchpad.net precise/main i386 Packages           
Hit http://ppa.launchpad.net precise/main TranslationIndex                              
Hit http://security.ubuntu.com precise-security/main Sources                                 
Hit http://security.ubuntu.com precise-security/restricted Sources                           
Hit http://security.ubuntu.com precise-security/universe Sources                          
Hit http://security.ubuntu.com precise-security/multiverse Sources                           
Hit http://security.ubuntu.com precise-security/main i386 Packages                           
Hit http://security.ubuntu.com precise-security/restricted i386 Packages                     
Hit http://security.ubuntu.com precise-security/universe i386 Packages                       
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages                     
Hit http://security.ubuntu.com precise-security/main TranslationIndex                        
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex                  
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex                  
Hit http://security.ubuntu.com precise-security/universe TranslationIndex                    
Ign http://ppa.launchpad.net precise/main Translation-en                                     
Hit http://security.ubuntu.com precise-security/main Translation-en                          
Hit http://gb.archive.ubuntu.com precise/main Sources                                        
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                    
Hit http://security.ubuntu.com precise-security/restricted Translation-en                
Ign http://extras.ubuntu.com precise/main Translation-en_GB                                  
Hit http://gb.archive.ubuntu.com precise/restricted Sources                                  
Hit http://gb.archive.ubuntu.com precise/multiverse Sources                                  
Hit http://gb.archive.ubuntu.com precise/main i386 Packages                                  
Hit http://security.ubuntu.com precise-security/universe Translation-en                      
Hit http://gb.archive.ubuntu.com precise/main TranslationIndex                               
Hit http://gb.archive.ubuntu.com precise/multiverse TranslationIndex                    
Hit http://gb.archive.ubuntu.com precise/restricted TranslationIndex                    
Hit http://gb.archive.ubuntu.com precise/universe TranslationIndex                      
Ign http://extras.ubuntu.com precise/main Translation-en                                
Hit http://gb.archive.ubuntu.com precise/main Translation-en_GB                         
Hit http://gb.archive.ubuntu.com precise/main Translation-en      
Hit http://gb.archive.ubuntu.com precise-updates/main Sources     
Hit http://gb.archive.ubuntu.com precise-updates/restricted Sources
Hit http://gb.archive.ubuntu.com precise-updates/universe Sources 
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Sources
Hit http://gb.archive.ubuntu.com precise-updates/main i386 Packages
Hit http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://gb.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/universe Translation-en  
Err http://gb.archive.ubuntu.com precise/universe Sources         
  404  Not Found [IP: 91.189.92.201 80]
Err http://gb.archive.ubuntu.com precise/restricted i386 Packages 
  404  Not Found [IP: 91.189.92.201 80]
Err http://gb.archive.ubuntu.com precise/universe i386 Packages   
  404  Not Found [IP: 91.189.92.201 80]
Err http://gb.archive.ubuntu.com precise/multiverse i386 Packages 
  404  Not Found [IP: 91.189.92.201 80]
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/main Sources   
Hit http://gb.archive.ubuntu.com precise-backports/restricted Sources
Hit http://gb.archive.ubuntu.com precise-backports/universe Sources
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://gb.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://gb.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://gb.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://gb.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/main Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/universe Translation-en
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.92.201 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
al@my_laptop:~$ 

```

So I then tried to browse to the directories that the updater is looking for, and this is far as I got. There is no 'Sources' directory here, but there is a Sources.bz2 and a Sources.gz. Is that what the updater is looking for, and if so why isn't it finding it? Or if there is supposed to be a Sources directory, why is it not there?

[http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/source/](http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/source/)

Likewise with 'Packages' here:

[http://gb.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/](http://gb.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/)

All of the directories in these links say they haven't been modified since 2012. But wouldn't directories on servers that we download updates from, be modified whenever new updates are released?

Thanks!

---

### Post by Al1000 on 2014-10-23
I received another system notification this morning telling me than an update is available. So I clicked on the notification and Muon Update Manager opened, asked me for my password and installed the update, which had something to do with daylight saving. But instead of saying 'your computer is up to date' afterwards, it said 'no updates are available. Last checked 4 days and 9 hours ago.' 

When I click on 'check for updates,' I get the same error message as I posted in the OP.

Does anyone know what's going on, or how I might go about finding out what the problem is?

---

### Post by westie457 on 2014-10-23
Hi, try changing the server via System Settings > Software and Updates > Download From......

I don't use Kubuntu so things might be slightly different to standard Ubuntu. Anyway this should point you in the right direction.

In a terminal ```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
The last one is not really necessary, only run it if some packages are being held back

---

### Post by Al1000 on 2014-10-23
> Hi, try changing the server via System Settings > Software and Updates > Download From......

I couldn't find anything in System Settings but I found an option in Muon Update Manager to 'Configure Software Sources,' so I changed download from 'UK server' to 'main server' and that did the trick. It now reports my computer as up to date.

> The last one is not really necessary, only run it if some packages are being held back

I have used the first two commands regularly, but as I mentioned in the OP, they didn't work yesterday. However they are working again just fine now that I've changed the software source.

I've never used the third command before, but I just ran it there, and it said nothing needs to be upgraded.

Contrary to what I said in the OP, I suspect that my computer might have downloaded and installed updates yesterday, before displaying the error message, just like it did this morning, as it hasn't downloaded any updates since I changed the software source. I sat and watched it update this morning, whereas yesterday I left it to install the updates after entering my password, and when I returned to the computer and saw the error message, I assumed it hadn't done so.

Anyway, many thanks for your help.

---

### Post by Mike_Walsh on 2014-10-23
Which of the UK servers are you using?

I don't tend to use the main one. I found out quite some time ago, by experimentation, that the two most reliable ones (for me, at any rate, in the East Anglia region) are:-

1) ubuntu.datahop.net, and
2) mirror.vorboss.net

I've had no problems at all with those two in the 6 months or more that I've been using the 'buntus....and I'm using all of them. I was in Kubuntu 14.04, two days ago, & I had just one glitch. I was installing the most recent updates, and for a few moments, Muon said the download had failed....and suggested the system might be broken! However, I think that was caused by my disconnecting from the #ubuntu IRC channel on Hexchat, at the same moment the download started; I'm running an old single-core Athlon 64, and it might have been just too much for it to handle simultaneously...I don't know. It usually multi-tasks just fine.

Anyway, try those two, and let us know how you get on.

Regards,

Mike.

---

### Post by buzzingrobot on 2014-10-23
The "404 Not Found..." in the OP is server lingo saying, in effect, " I can't find what you are looking for."  It's what servers return when, for example, a browser makes a request to download a file that isn't there.  In this case, the updater was asking to download files that either were not on the server, or the server couldn't locate for one reason or another.

---

### Post by Al1000 on 2014-10-24
> **Mike_Walsh said:**
> Which of the UK servers are you using?

I don't tend to use the main one. I found out quite some time ago, by experimentation, that the two most reliable ones (for me, at any rate, in the East Anglia region) are:-

1) ubuntu.datahop.net, and
2) mirror.vorboss.net

I've had no problems at all with those two in the 6 months or more that I've been using the 'buntus....and I'm using all of them. I was in Kubuntu 14.04, two days ago, & I had just one glitch. I was installing the most recent updates, and for a few moments, Muon said the download had failed....and suggested the system might be broken! However, I think that was caused by my disconnecting from the #ubuntu IRC channel on Hexchat, at the same moment the download started; I'm running an old single-core Athlon 64, and it might have been just too much for it to handle simultaneously...I don't know. It usually multi-tasks just fine.

Anyway, try those two, and let us know how you get on.

Regards,

Mike.

I'm not sure which server I'm using; it just says "main server." How would I find out which one it is?

I also have Kubuntu 14.04 on my other computer, and it is also configured to use "server for the UK" although I haven't had any problems with it. I now see the drop down list of servers including the two you mention when I select "other," but it doesn't say which one I'm currently using.

---

### Post by Mike_Walsh on 2014-10-24
Hi, Al.

I must confess, I don't know myself which the main server is, OR where it's located..! As far as I know, the others are alternatives to the main one, depending on your location, and the speed of return of the 'ping' test.

I just know that I ran the ping test quite a few times. You don't always get the same one come up each time (depends a lot on how many people are using broadband at any given moment in your area), but those two, and 'ubuntu.datahop.net' in particular, came back as the server for me to use more often than any other, so I've permanently set ALL my distros to use it.

That would be the best way to see which is the best 'mirror' for your area. Run the test, say, 10 times in a row; and whichever one shows up more often than the others, I would set that as my download server. Simples!

The failure of your download on that particular occasion could well have been a one-off glitch; internet connections are subject to an awful lot of variables (number of people on the line, what they're doing, how much they're downloading, etc.).

Regards,

Mike.

---

### Post by Al1000 on 2014-10-24
I had just stuck with whatever server Kubuntu decided to use when I installed it, and had never noticed the ping test.

I've now run it and it selected mirrors.melbourne.co.uk

```
al@my_laptop:~$ host mirrors.melbourne.co.uk
mirrors.melbourne.co.uk has address 92.63.142.155

al@my_laptop:~$ curl ipinfo.io/92.63.142.155
{
  "ip": "92.63.142.155",
  "hostname": "No Hostname",
  "city": "Melbourne",
  "region": "Derbyshire",
  "country": "GB",
  "loc": "52.8167,-1.4333",
  "org": "AS39451 Melbourne Server Hosting Ltd."
```

Now I'll go and do the same on my other computer and see if it picks the same server. Thanks for your advice.

---

### Post by Mike_Walsh on 2014-10-24
Well, that's the idea of the forums, of course. We help each other out with tips, tweaks, suggestions, advice & work-arounds. I've helped you out with this; in turn, someone else has helped ME with a sticky problem earlier on today. 

You scratch my back, & I'll scratch yours, etc.....

Glad I could help.

Regards,

Mike.

---

