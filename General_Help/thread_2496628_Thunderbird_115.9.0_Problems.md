---
title: "Thunderbird 115.9.0 Problems"
date: 2024-04-05
forum: General Help
---

### Post by hennmann on 2024-04-05
Hi again everybody
I'm having problems with my Thunderbird email client and recently, I changed  my email password and it is working on everything except my Thunderbird on my Ubuntu.
Okay I reset my password and checked all of my incoming and outgoing mail server settings including assistance from my Internet/email provider tech service and all is good. 
I reentered my correct password when I get the Password Required-Mozilla Thunderbird
? Please enter your Primary Password

I enter my new password for my email account and press the blue Sign in button Icon and blip this window keeps reappearing with an empty box and keeps prompting me for a password.

A number of months ago I had account password problems and I was unable to recieve and send emails on my Thunderbird and the only way I, and my service provider could get it to work was for me to remove my email account from my Thunderbird  email client and re enter it and this worked. This time I think I actually deleted it and reentered and I keep getting the password window popping up.
What am I doing wrong and it appears my contacts are still within Thunderbird.
Do I have to remove and reinstall Thunderbird or am I missing a step here?
I advised tech support it was Thunderbird on Ubuntu and he mentioned he was familiar with it as well. 
Perhaps this isn't a password problem from the recent password change and perhaps it's a Thunderbird glitch?? A different problem misleading me to thinking it's my password change perhaps? 

A bit more info here is I routinely update my system and there are current updates available including the notification pop up telling me a new version is available but this happens at the most inappropriate times and I select ask me later. Otherwise I have the Cougar on my Desktop

IF removing and reinstalling is perhaps a solution, how do I backup my contacts list? Since my server settings are IMAP I can download all my emails from the server as well.

---

### Post by hennmann on 2024-04-06
Currently I posted this problem on Mozilla forum and waiting for assistance and also included all the port and server settings which are correct.
IF my Thunderbird installation is "buggy" what is the proper Ubuntu procedure for backing up my contacts and uninstalling and reinstalling the latest version of Thunderbird?

---

### Post by gezzer2 on 2024-04-06
you can use Thunderbirds own settings to export contacts ( i cant remember exactly where as i haven't used TB in a long time).
just as a matter of interest are you using the snap of TB or the .deb install as i have found that sometimes the .deb file install works better then the snap ..

---

### Post by him610 on 2024-04-06
IDK if this will help or not, but my Thunderbird gets its email through Comcast/Xfinity, and to configure Thunderbird to receive/send email, one must use the comcast/xifinity email password.

---

### Post by hennmann on 2024-04-06
My provider is Saskatchewan's Sasktel and they are our internet, email and telephone land line provider and of course we have Sasktel webmail where we use a browser to log on directly on the Sasktel server using a web browser. Let's say my computer or internet goes down I can log on there and of course directly change my password there. I also have 3gb of space on their server for each email account and of course if you send lots of pictures, and if that 3gb gets filled, you have to log on using a browser and go through all emails and delete ones you don't want and then after that empty the deleted emails folder and then delete the trash folder contents. This or you cannot send or recieve. 
Using their IMAP Server settings 
Incoming Server
IMAP Server
mail.sasktel.net
Security Type
SSL
Port 
993

Outgoing Server
SMTP Server
smtp.sasktel.net
Security Type
TLS
Port
587
Require authentication to send emails (turned on)

And of course on Outlook Express which is used on my Windows 10 partition of my dual boot computer of which Ubuntu is also on, my Outlook requires me to enter the same password on both Incoming and Outgoing servers which is the password my Sasktel server requires to be accessed. 

In the case of this Thunderbird, the password has to be entered and even though I selected "remember password" it still pops up the window Enter Passwrod and when I do, it doesn't carry on and then start downloading emails but instead it keeps popping up the enter password window repeatedly. 
On my Outlook I have the option of it remembering or to have to enter it for both receiving and sending email. 
I suspect my installation of Thunderbird has turned into a Thunderchicken and perhaps the software is corrupted?

---

### Post by gezzer2 on 2024-04-07
for the outlook login you may need an extension/add on. 

tbsync
[https://addons.thunderbird.net/en-GB/thunderbird/addon/tbsync/?src=dp-dl-dependencies](https://addons.thunderbird.net/en-GB/thunderbird/addon/tbsync/?src=dp-dl-dependencies)

and possibly
 
caldev
[https://addons.thunderbird.net/en-GB/thunderbird/addon/dav-4-tbsync/?src=ss](https://addons.thunderbird.net/en-GB/thunderbird/addon/dav-4-tbsync/?src=ss)

also have a look at this Thunderbird and outlook
[https://support.mozilla.org/en-US/kb/microsoft-oauth-authentication-and-thunderbird-202](https://support.mozilla.org/en-US/kb/microsoft-oauth-authentication-and-thunderbird-202)

have a look at these and see if they help ..

---

### Post by hennmann on 2024-04-08
Outlook is fine, my Sasktel Web email is fine, my android phone is fine as well. Thunderbird asks for my password and just keeps popping up the window as if no password is entered or a wrong password is entered over and over. Is there a way to uninstall it and reinstall it? Is there an alternative to Thunderbird?
I have had problems like this with it before and now I cannot correct it and if I cannot correct it, it is no different than having no email client.

---

### Post by hennmann on 2024-04-08
I might add that when I had my service provider tech support on the phone, he asked me if I had VPN running and I said and it never created a problem before. I even disabled it, reinabled it and the password window keeps popping up! 
Alternatives to Thunderbird?
How do I uninstall Thunderbird and then reinstall it?

---

### Post by gezzer2 on 2024-04-08
i have find this. it looks like MS have changed the log in requirements ..

[https://support.mozilla.org/en-US/kb/microsoft-oauth-authentication-and-thunderbird-202](https://support.mozilla.org/en-US/kb/microsoft-oauth-authentication-and-thunderbird-202)

---

### Post by hennmann on 2024-04-08
Bear with me here!!
Let me throw everything out in the open here as well for clarification.
I  DO NOT USE HOTMAIL and avoid it like the plague it is because why do I  want to wade through tons of SPAM GARBAGE DAILY? In order to use that  garbage you have to put up with this so lets get Hotmail out of the  picture.
I have Microsoft One Drive but I couldn't be bothered to pay  for space above and beyond this nonsense when I have tons of hard drive  space  on my computers and memory on my phone. This is just another  money grab just like iCloud and due to having a garbage iPhone for years  with no storage space I now have a Samsung Note 20 Ultra with 512gb of  storage and it can handle a 1TB SD card.
Microsoft has NOTHING to do  with my Sasktel email and internet service provider and this also  includes Hotmail and Gmail and yes I also have Gmail but seldom use it.
Why  am I using Linux? When Microshaft dictates that my 2017 AM3+ hardware  including an FX8570 8 core processor are not compatible with their  garbage Win 11 which has very little difference between Win 10 except  uses more disk space and RAM is when I look for alternatives.
Sasktel is totally independent and works on all of my devices.

Now  I will now get back to the point of all my settings are correct and  nothing has changed except my password of which this 115.9.0 will not  except. I went through this nonsense a number of months ago and the only  way I could get this CRAP to work was literally remove my email account  from TBird and reinstall it and it worked back then but not now.  Sasktel tech support suggested that step months ago and now it doesn't  work at the present time. This time the Sasktel tech agent asked if I  have VPN running and I beat him to this and disabled it and this didn't  solve the issue and I advised him of this being done and it wasn't an  issue before.
Obviously this installation is buggy or corrupted  perhaps during a software update, and I wish to uninstall it and  reinstall it and start over!! If it doesn't work II will rip it out and  look for an alternative. As for SNAPS,  I'm totally unfamiliar with this  concept and even though I started using Linux over 20 years ago and of a  number of different distros, some of which do not exist anymore, I have  limited knowledge of commands on the Terminal.
Now given all of this, how do I uninstall Thunderbird and then reinstall it?
If  after all of this kerfuffle, it still doesn't work, what is a great  alternative other than using Windows for email? As it is, if I wish to  do online transactions I generally use Linux with fewer worries of  security and viruses.
BTW, how long does it take to reset my Sasktel  email server password in Outlook, and on my Note 20? a matter of a few  seconds to access my account settings to simply backspace and delete the  existing email and type in my new password and it is done. This also  includes all of my server settings for incoming and outgoing mail as  well. During situations like this, I also test my password to see if it  is actually proper by using a browser and logging onto Sasktel Webmail  and go directly to my account on the Sasktel service provider's server  and also Sasktel is our provincial government telephone and  internet/email service provider if you don't wish to use Hotmail or  Gmail and is like using one of those American service providers.

---

### Post by #&amp;thj^% on 2024-04-08
> **hennmann said:**
> 
Now given all of this, how do I uninstall Thunderbird and then reinstall it?


First for your back-ups for Tbird: [https://www.technewstoday.com/how-to-backup-and-restore-thunderbird/](https://www.technewstoday.com/how-to-backup-and-restore-thunderbird/)

To uninstall it completely for 20.04 and 22.04 use
```
sudo apt autoremove --purge thunderbird
```

Check in your home directory with {Ctrl + h} reveals hidden folders and in .mozilla folder look for thunderbird to see if anything remains.
Good Luck

---

### Post by hennmann on 2024-04-08
Here is another discovery and I also upgraded my system to 22.0.4
After the upgrade Thunderbird is still messing around and i reinstalled my account and it still wont accept my password. The blue +New Messages box is instead of being deep blue appears faded as if this function is disabled and of course it is because IT WON"T ACCEPT MY PASSWORD!!
I go into my Ubuntu Software and select Installed Software and Thunderbird doesn't appear including Mozilla Thunderbird so I cannot even uninstall it even though the icon is on my Desktop so what is up with this??
Yes I tried different settings and as it is the settings for Authentication aren't even exact with what is on Sasktel  port settings including authentication or port security.
HOW DO I REMOVE THIS QUESTIONABLE SOFTWARE AND START OVER??
How do I uninstall if it doesn't appear in the Ubuntu installed software? How does something allegedly not installed still open up and attempt to work even though it is not indicated in my Ubuntu installed software? Firefox We Browser sure as heck does and appears in this location.

---

### Post by #&amp;thj^% on 2024-04-08
Software center shows snaps, and if truly using 22.04 is a .deb
ie:
```
apt policy thunderbird
```
Should show up there ie:
```
apt policy thunderbird
thunderbird:
  Installed: 1:115.9.0+build1-0ubuntu0.23.10.1
  Candidate: 1:115.9.0+build1-0ubuntu0.23.10.1
  Version table:
 *** 1:115.9.0+build1-0ubuntu0.23.10.1 100
        100 /var/lib/dpkg/status
     1:115.8.0+build1-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 Packages

```

You say you upgraded to 22.04, but did you follow or try my suggestions in post #11

My removal:
 ```
The following packages will be REMOVED:
  thunderbird* thunderbird-locale-en* thunderbird-locale-en-us*
0 upgraded, 0 newly installed, 3 to remove and 255 not upgraded.
After this operation, 258 MB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 298101 files and directories currently installed.)
Removing thunderbird-locale-en-us (1:115.9.0+build1-0ubuntu0.23.10.1) ...
Removing thunderbird-locale-en (1:115.9.0+build1-0ubuntu0.23.10.1) ...
Removing thunderbird (1:115.9.0+build1-0ubuntu0.23.10.1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1.1ubuntu1) ...
Processing triggers for man-db (2.12.0-3) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu5) ...
(Reading database ... 297994 files and directories currently installed.)
Purging configuration files for thunderbird (1:115.9.0+build1-0ubuntu0.23.10.1) 

```

 I think there is more to this than meets the eye....

---

### Post by hennmann on 2024-04-08
Since no replies showed up I did searching at other websites to uninstall it and used command line to remove and to also reinstall it and also had to get the snap. Yes it installed and is back to square one.
1fallen, my previous search gave me this 
sudo apt autoremove --purge thunderbird

but since I did this before reading your post I didn't do this
"Check in your home directory with {Ctrl + h} reveals hidden folders and 
in .mozilla folder look for thunderbird to see if anything remains.

Good Luck"

One thing I noticed is my address book still remained intact so I guess I should repeat including following your steps.

Like I mentioned earlier Bear with me and I will mention a big thank you to everybody as I stumble through this! It looks Like everything didn't get purged so I will start over. I will let you know what the results are. Other than this, with this latest glitch I never had any problems with Thunderbird before except for my previous problems a few months ago

---

### Post by hennmann on 2024-04-08
sudo apt autoremove --purge thunderbird                       gave me this response

Do you want to continue? [Y/n] y
(Reading database ... 184387 files and directories currently installed.)
Purging configuration files for thunderbird (1:115.9.0+build1-0ubuntu0.22.04.1) ...
dpkg: warning: while removing thunderbird, directory '/etc/apport/native-origins.d' not empty so not removed
don@krait:~$ 
I followed your search and I deleted everything except the folder mail.sasktel.net which contains Sent and inbox containing 3.2gb of emails so perhaps I should save it elsewhere.

---

### Post by #&amp;thj^% on 2024-04-08
If all else fails it available as a flatpak as well, and recommenced by Mozilla
> Install from Flatpak (Recommended)
[https://support.mozilla.org/en-US/kb/installing-thunderbird-linux](https://support.mozilla.org/en-US/kb/installing-thunderbird-linux)

Just let me know how you want to proceed.

My time today is short, leaving for the Airport very soon for a day or two.

And you can access your mail through a browser as well....just a reminder.

---

### Post by hennmann on 2024-04-08
Only one folder was remaining with my mail.sasktel.net folder moved to my documents folder and then I went back to Terminal and entered sudo apt install thunderbird
My icon appeared back on my favorites and back to square one LMAO......................................!
I went back to home directory and then to Mozilla including Turdbird directory and everything was back in there as if it was never removed. This is so sad its totally laughable. 
After I read your link  [https://www.technewstoday.com/how-to-backup-and-restore-thunderbird/](https://www.technewstoday.com/how-to-backup-and-restore-thunderbird/)     I will determine how to back it up and just in case I @#$% things up I will take that folder in Tbird and save it to a flash drive.
BTW!! Just to be clear on what is now going on AFTER the Terminal command of sudo apt install thunderbird, I selected Control H as you instructed and yes I see my .thunderbird directory  and below this clearly shown folder is faded out or perhaps so called hidden folders:
examples.desktop
.bash_history
.bash_logout
.bashrc
.ICEauthority
.profile
.sudo_as_admin_successful

After the sudo apt autoremove --purge thunderbird command and returning to the home directory and of course using Control H, what should there be remaining? If there is something remaining do I delete it? or...................get out my hard drive utility and do a low level format to the drive writing zeros and then ones to each and every sector LMAO!

"To boldly go where no man has gone before"

---

### Post by #&amp;thj^% on 2024-04-08
Just delete anything ".thunderbird"

Are you ready for a flatpak install?

Time has ran out for me today, got to catch a Jet.
I'll check back after i land.

---

### Post by hennmann on 2024-04-08
Hi and thanks again on "delete anything Thunderbird"
I can wait until you land ans hopefully it's not a Boeing 737max&#129315;&#128591;.
Anyway after taking a break from this I contacted Sasktel tech support just to make absolutely sure everything is set up properly and this is also a wise step because I could be wrongfully blaming Thunderbird! 
What was totally bothering me were the security settings for passwords which are slightly different for Thunderbird vs Outlook and my smartphone. I tried both Autodetect and Normal Password which were not suggested on Sasktel email support website for setting up the email client and Sasktel tech support told me
" either Normal or Auto detect will work fine" "and the port settings and SSL & TLS used in Outlook and my Samsung are perfectly fine on Thunderbird"
The Tech support staff I find are using both Outlook and Thunderbird and most likely use both so they are familiar with both. Yes they asked me if I was using VPN and I told them I disabled it as well. Besides this VPN is on my Windows as well with no problems and besides this it wasn't a problem before. 
Given all of this, most likely my Thunderbird is corrupted with a glitch..
As per your instructions I will go back and uninstall and completely purge everything&#128591;and give it a try. It will be easy to determine if properly purged because what reappeared was folders with 2019, and 2022 dates along with all other folders so a total purge didn't occur just like removing a virus on Windows&#129315;. 

One thing is for sure and this is quite a learning process including using commands on a terminal. Using Windows for years has turned me into a GUI slave. During my search for information on removing Thunderbird, other people also mentioned what I also discovered and that was Mozilla Thunderbird is not showing up in Ubuntu software where you select uninstall and is where I saw the Terminal command to remove it as well as reinstalling it.
Also my upgrade from 20.4.0 to 22.4.0 went smoothly as well. The pop-up that advises me a new version is available always appeared at the most inappropriate times so I did an upgrade using terminal commands.

---

### Post by hennmann on 2024-04-08
1fallen

I once again did the uninstall as per your instructions and again went into home directory and located Thunderbird and deleted it. The faint folders bellow this folder I sat and looked at and looked at carefully including reading the text and they were nothing to do with Thunderbird so I stayed away from them because they are likely important system files!!
I reinstalled and it indicated TBird was installed but no icon on desktop and no indication of it in Ubuntu installed software, just to discover the icon was in the same Applications directory lol so I moved it to favorites.
Well now we have a different situation here!!! It is now showing no account and I entered the proper settings including my password and like before checked off the blue box "remember password including using Auto detect and after hitting re test and save my emails started downloading.I moved the entire folder prior to the uninstall and purge and as it ended up their instructions as per your provided link were similar to what I did but I saved even more. My address book and contacts are empty as it stands but I will restore them later on. Most likely there was a way I got them there in the first place before my dual boot so I will look into this as well.
One thing is for sure and that is IF Thunderbird was working before with the settings I had, they were most certainly correct! Obviously the software got corrupted and this likely started several months ago getting progressively worse.

---

### Post by hennmann on 2024-04-08
> **1fallen said:**
> Just delete anything ".thunderbird"

Are you ready for a flatpak install?

Time has ran out for me today, got to catch a Jet.
I'll check back after i land.

Something for me to consider and I will look into it now that I got most of my Thunderbird problems straightened out.

---

### Post by dragonfly41 on 2024-04-09
> Anyway after taking a break from this I contacted Sasktel tech support just to make absolutely sure everything is set up properly and this is also a wise step because I could be wrongfully blaming Thunderbird!


I suspect that this is true .. wrongfully blaming Thunderbird.


Regard this as an exercise in navigating and learning Ubuntu.
Personally I see these popups every day. I just click through Cancel and get into Thunderbird GUI.
I would think twice about reinstalling. You might jump from frying pan into fire.
Instead use this case to refine your troubleshooting skills.
My first thought is to ensure that you have backed up your existing setup. This takes you into a different world. Search rdiff-backup.


Another option is to have a second Thunderbird profile for testing.
[https://support.mozilla.org/en-US/kb/using-multiple-profiles](https://support.mozilla.org/en-US/kb/using-multiple-profiles)
[https://support.mozilla.org/en-US/kb/profiles-where-thunderbird-stores-user-data](https://support.mozilla.org/en-US/kb/profiles-where-thunderbird-stores-user-data)
[https://support.mozilla.org/en-US/products/thunderbird](https://support.mozilla.org/en-US/products/thunderbird)
Other apps such as Firefox allow multiple profiles.
The process is explained here.
[https://support.mozilla.org/en-US/kb/using-multiple-profiles#w_starting-the-profile-manager](https://support.mozilla.org/en-US/kb/using-multiple-profiles#w_starting-the-profile-manager)
Returning to Thunderbird go to top bar > Help > Trouble Shooting Information
Study the data.
In particular view the table:
**Mail and News Accounts**
In my Trouble Shooting I look to **Outgoing Servers** and I see that i have No Authentication on some accounts. This might explain why I see the pop messages at Thunderbird startup.
There is **“Diagnose Issues”**
You can switch to **"TroubleShoot Mode"**.


But note I have had no cause myself to dive in here. And I only have one Profile.


I might consider diving in deeply.
To backup profile.
[https://support.mozilla.org/en-US/kb/profiles-where-thunderbird-stores-user-data#w_how-do-i-find-my-profile](https://support.mozilla.org/en-US/kb/profiles-where-thunderbird-stores-user-data#w_how-do-i-find-my-profile)
Yet another option is to run Thunderbird in a virtual machine on your desktop.  Or perhaps use your LiveUSB to “Try Ubuntu” (not install) to observe how Thunderbird works in a fresh environment.

---

### Post by hennmann on 2024-04-09
I could not enter my correct password after following 1fallen's 
sudo apt autoremove --purge thunderbird
And it was simply a totally repeat of the problem at hand. 
After he advised me to go into .home directory including Control H to reveal hidden folders and TOTALLY CLEAN OUT THUNDERBIRD, EVERYTHING THUNDERBIRD, was when I was able to reinstall a "clean" installation and get it to work. 
Unless you ferret everything out  and by everything I mean EVERYTHING, you will get a repeat! 
You should NOT have to remove your entire account such as your entire email account in order to get it to work and this was the case 2 months ago and that is the ONLY way it would accept.
Fast forward to the present time, not even all of these needless steps would help.

If software was so perfect we wouldn't need updates and perhaps my Tbird became corrupted during an update? 
2 months ago a friends email account was hacked during an attempt at fraud and all his contacts were sent an email requesting they purchase gift cards for a sick friend and I suspected his account was hacked and contacted him by phone to enquire. 
You guessed it! This prompted me to change my password as well and back then it was remove my account in order to finally get it to work! For security reasons is why you should change your email account password on a routine basis! 
Now again I change it and this happens and if this is normal for Thunderbird, which I doubt it, it should be a simple procedure only taking a few minutes!! On my Windows 10 where I use Office 2007 Professional which uses Outlook, I go into my email client, into settings, account settings, over to server settings including password and backspace or delete, enter new password and enter save and it is done! The same applies to my service provider server where I log on using a web browser and of course my smartphone. 
When ALL your server settings are correct including password, including checked and rechecked a number of times, and then correct password promptly rejected, there is a problem.

On Thunderbird Support forum one member scoffed at totally removing everything when he said all I had to do was remove my email profile and account and re-entering it instead of wiping it all out. I CLEARLY pointed out THAT DIDN'T WORK until I did what 1fallen mentioned and that was to go directly into the .home directory and TOTALLY ferret out ALL THUNDERBIRD and that is THE ONLY WAY I got it to work. Using the uninstall/purge command did not get it all out and purge/uninstall and reinstall only recreated a problem because all of my folders dated 2018 and later reappeared like a reoccurring nightmare&#129315;. 
Perhaps there was nothing wrong with the TBird software, but one of those folders within contained something that caused it to not work.
Passwords should be routinely changed for security and it should be a simple procedure to do so&#129300;. 
Oh yes as mentioned to 1fallen, to really be sure I wasn't pointing the finger at the wrong problem, I again contacted Sasktel to verify and clarify the "autodetect" or "normal password" settings and they advised both are perfectly fine. I also experimented with both prior to total removal with no success. 
Total purge, cleaning out everything and it only took seconds to enter everything back in and save and instantly my emails came rolling back in from the server. I spent a number of days including with Sasktel tech support with no results attempting to get the previous installation to work.

It was less work to quickly move my mail.sasktel.net folder containing my contacts and emails to another directory and then totally purge out the entire installation including ALL folders and reinstall. 

If you see the identical situation that I had, this should be suggested and exactly like 1fallen mentioned but as it turned out my so called backup was more extensive compared to what his link mentioned. 
If software was perfect we wouldn't need updates. 
If my email account was hacked, this would probably be a good safety measure as well?? How easy would it be to plant a bug in my Thunderbird or did my bird get bird flu&#129315;

This has taught me more valuable lessons on how to do this and I even updated 20.4.0 and then upgraded to 22.4.0 using terminal including routine updates because the notifications always happen at the wrong time and take to long  reappearing when I select "ask me later" and what I need is more experience using commands because years of windows, as far back as Windows 3.1 has turned me into a GUI slave&#128514;.

---

### Post by #&amp;thj^% on 2024-04-10
Timeline, I'm sorry it took so long to get back to you, but things happen.

It sounds like you had quite the adventure, and gained some trouble shooting skills along the way.

And you also got a taste of what one person suggests will be Scoffed by another person. Typical response for what works for one is not the case for all.

Many many ways to accomplish things or tasks at hand.

Warning at times I'm known for swinging a big hammer as last resort. (Not recommended unless you know how to fix broken stuff)

---

### Post by hennmann on 2024-04-10
1fallen
Fantastic! A great, accurate response, and  in reality you summed it up very well&#128077;. The scoffers likely have never changed their passwords in many days, weeks, months, or even years and sometimes I'm guilty of this with my Sasktel password being the same for years and it was a simple 6 character figure provided by my service provider as a starting point&#128514;. 
When you never change or are forced to change passwords and things keep ticking along just fine, but that doesn't mean they are okay!! 
Going back several months when my friends account was hacked, I became suspicious when all my devices were acting glitchy and in reality it was Sasktel's server which was going through upgrades including converting over to 5G server as well. I got notices about "unable to connect with server" and damn it anyway it was a password situation and here is the laugh making me realize it was on their end! I selected reset password and just out of curiosity I reentered my current password and WTH it logs on?? Obviously a glitch on their server and everything now works and how did I determine this? When everything conks out at the same time I used my internet browser and logged onto my Sasktel webmail server account and discovered the problem. It is no use poking around in your email client on the phone or all your computers first but go directly to my service provider first and of course part of my Thunderbird diagnostics included this as well as rechecking all server settings. 
Let's face it! Are we going into our settings everytime we log onto our server? If you have "remember my password" selected this is done automatically and if you don't, everytime you open your email client you have to enter it.

Just out of curiosity I dug out my netbook, a pathetic Acer Aspire One 533 which in reality should be called an Acer Dispair Plenty 666, with a HORRIBLE Atom 455 single core processor and from new it was a gutless POS I should never have purchased&#129324;. It had 1gb of RAM and could barely handle Win 7 Starter Edition, a stripped down version and installing the maximum possible 2gb of RAM, which is still pathetic but helped,  is a daunting task with Acer describing it as unserviceable for an option but it is&#128514;&#128078;. 
Anyway I got Q4OS on it because right out of the box it is a nice lightweight distro that performs the best without looking totally stripped down and Ubuntu lite versions were more demanding on this gutless turd.
Yes it is using Thunderturd as well but an older? 102.9.0 32 bit and I never set it up. I went through the same song and dance and of course selected "remember password" and while sending and recieving mail it prompted me for a damn password&#129315;. Well anyway my password when entered does work&#128591; so even though it's supposed to remember, it has dementia and cannot remember it&#128514;. Best be leaving it as is or history will likely repeat&#128514;&#128591;. 
Other than this 1fallen you were extremely helpful in all steps from start too finish! 
Before I read your instructions about going into the hidden folders and ferreting out EVERYTHING, the automatic uninstal/purge left nasty reminants behind and it simply kept re-installing the same problem over and over. 
There is definitely a problem and I could have spent time attempting to try to determine what is wrong, but when you don't go into settings and disturb and it quits working is time to take a sledge hammer and rip it out by the roots. 
When I see this same problem, I will post my situation and obviously when all the proper settings are used and it still &#129326;, tells me to uninstall and try to reinstall and &#128591;. 
If nothing is disturbed it should keep functioning.

---

### Post by hennmann on 2024-04-12
Here is the latest update on this Thunderchicken&#129315;situation.
Today I log onto my email with my cell, a Samsung Note 20 and immediately it complains it cannot log onto the server? Oh really? Here we go again&#128545;.
I go straight over to my Sasktel web email server and use this newly created password and yes it's correct and no I cannot log on. I contact Sasktel tech support and explain this entire situation, reset my password yet again&#128514; and after this is done tech support checks my account, at my request for a recent password reset or request for one and there is none and no signs of any suspicious activity and we both agreed there was perhaps a glitch in the server because I didn't use an incorrect password. 2 months ago this happened and I selected reset and for an experiment I entered my recent rejected password and it now works&#129300;. I mentioned this to tech support as well.
Fast forward to Thunderbird and the fact that several months ago I had to TOTALLY remove my account from Thunderbird in order to get it to work, and recently my password reset failed in every attempt including uninstalling and the mess repeating until 1fallen mentioned how to totally clean everything out and then reinstall.
Now we have this password situation and my thought was here we go again&#128534;&#128514;.
I opened Thunderbird and again it complained like everything else, that it couldn't log on with the window popping up to enter password and I deleted the password and entered the new recreated password and selected remember password and &#128591;&#128591;&#128591;clicked save and it downloaded all emails needing to be downloaded. 
I did my usual test of sending a test email to myself and of course it prompted me for a password on the Outgoing Mail Server and again I entered and it accepted and saved it.
Of course a reboot into Windows to reset Outlook as well and then back into Ubuntu and it logs on without a password required prompt. 

This clearly indicates the former installation was corrupted in some way and without any server setting changes made, it should remain this way. If one is learning how to use Ubuntu and this Thunderbird, back it up like I did and rip it out as per 1fallen's instructions&#129315;. If I was a heavy duty advanced Linux user with all commands in my memory as if I know a second language, well perhaps attempt to figure out what is going on but if all else fails treat it like a software update and yank it out and reinstall. If one doesn't know how to properly go into this software and determine the problem and then attempt to make changes, this could be "jumping into the fire from the frying pan"

---

### Post by dragonfly41 on 2024-04-13
Have you perused Troubleshooting Information as penned in post #22?

---

### Post by hennmann on 2024-04-13
I have used a number of the suggestions in that post but in reality:
My port and server settings NEVER CHANGED
I removed and reinstalled my account 2 months ago after much difficulty to finally get it to work. Two months later this never worked!! 
Obviously if it takes me just seconds in identical circumstances to change password, there was something wrong. When you use it day after day for literally months and then a password gets changed, and it is a major problem to enter a new password, there is something major wrong and yes I always update. You shouldn't have to change profile and do a major song and dance if all of a sudden you need to change a password and in reality, saving a backup, uninstall with full purge and checking if anything remains behind was faster once I knew what to do. I sure as heck don't have a computer science or Electrical Engineering degree and I feel I shouldn't have to diagnose somebody else's software and I do this often enough when a Windows update goes wrong installing wrong drivers and other problems.

---

### Post by dragonfly41 on 2024-04-13
I agree that you should not have to jump through such hoops. I have used Thunderbird on multiple domain accounts for years and apart from the annoying password popups (probably I have a password glitch) it continues to work.  I just cancel the popups and leave well alone. If I experiment it will be in a virtual machine.
Recently I experienced a spate of spam flooding coming into a dormant account. This was not Thunderbird problem. I had to tighten the security in my domain managed by Google. MX records. So what might appear to be a Thunderbird issue in fact might come from another source. [Sasktel]("https://support.sasktel.com/app/answers/detail/a_id/15455")? Or domain DNS records?

---

