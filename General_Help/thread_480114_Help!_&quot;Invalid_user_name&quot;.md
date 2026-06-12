---
title: "Help! &quot;Invalid user name&quot;"
date: 2007-06-21
forum: General Help
---

### Post by ljk on 2007-06-21
Help, please.

I downloaded Wubi and ran the installer without realising that only lower case letters could be used in the user name.

On Restart ->Ubuntu, Wubi tries to load/install/setup things but after a few minutes I get an error message that an invalid user name was entered and which has "continue" at the bottom. Clicking space bar and/or Enter have no effect and I have been forced to use the power on/off button to shutdown.

I tried running Wubi again and changed the user name but the same thing happened.

I could just delete everything and download again - taking more care this time not to accept the user name which automatically appeared (same as my Windows user name) but if there is an easier work around I'd appreciate any info about it.

Thanks.

---

### Post by ago on 2007-06-21
> **ljk said:**
> Help, please.

I downloaded Wubi and ran the installer without realising that only lower case letters could be used in the user name.

Hmm you should not be able to click the install button if you use upper case letters in the username. What version of wubi did you use?

---

### Post by ljk on 2007-06-21
Today's.

 I was so impressed by Wubi on my home machine that I downloaded & installed it on a PC I have at the office shortly before I posted my plea for help.

I got the nice new interface (a separate post  in the feedback forum expresses my thanks) and just went ahead with choosing the other options but should have suspected that having my user name appear automatically could only come from detecting the current user account's name in Windows. That was in upper & lower case characters.

When the installation process stalled on "Invalid user name etc." I tried the instructions at the bottom of the screen [Tab to change/Spacebar to select/Enter to apply??] - the only "button" available was "Continue". I used "spacebar", then I used "Enter" ; no luck. So then I tried again allowing a few minutes to pass between the clicks. Same screen for 20 minutes.

It's not a huge problem to just delete everything and start again from zero but it just seems like a waste of resources if there is a way to reset the user name without chanting spells & killing chickens.

Many thanks for asking.

Best regards.

---

### Post by ago on 2007-06-21
> **ljk said:**
> I got the nice new interface (a separate post  in the feedback forum expresses my thanks) and just went ahead with choosing the other options but should have suspected that having my user name appear automatically could only come from detecting the current user account's name in Windows. That was in upper & lower case characters.

Hmm the windows username should be converted to lowercase letters. At least in wubi-7.04.01. I'll doublecheck that anyaway.

---

### Post by ljk on 2007-06-21
Many thanks.

I don't know if this is important but my Windows OS is the Japanese version of XP Professional.

Best regards.

---

### Post by CrazyGuy123 on 2007-06-21
You don't have to re-download the files - You can uninstall wubi and choose to backup the downloaded files, so you don't have to download again.

---

### Post by ljk on 2007-06-22
> **CrazyGuy123 said:**
> You don't have to re-download the files - You can uninstall wubi and choose to backup the downloaded files, so you don't have to download again.

Thanks. I'm not sure I understand what to do, though.

I use the Windows control panel to uninstall Wubi (???) and then what do I do - is there an option to backup the files in the uninstaller? Wouldn't the file containing the problem user name also be backed up?

Sorry to be so ignorant in these matters but I appreciate your post and would be much obliged if you could enlighten me. I feel sure that I will not be the only novice to need a "How To..." get back to the point where downloads have been completed and installation is about to start.

Many thanks indeed for the above info and for any further help you can offer.

Best regards.

---

### Post by ago on 2007-06-22
> **ljk said:**
> I use the Windows control panel to uninstall Wubi (???) and then what do I do - is there an option to backup the files in the uninstaller? Wouldn't the file containing the problem user name also be backed up?
Yep you uninstall as any other app. When you uninstall a dialog comes up where you can select to back up the ISO so you do not have to redownload it when you reinstall

---

### Post by ubmajumda on 2007-06-22
well, I had the same problem, and I backed up the program when I uninstalled it. 

will the installer, when run again recognize the backed up files, or will download all over again?

---

### Post by ago on 2007-06-22
yes, it will find the wubi-save folder and use the files in there

---

### Post by ubmajumda on 2007-06-22
thx

---

### Post by trelos on 2007-06-22
I'm having the same problem... when I get the error message I can hit escape and it looks like it is hanging up on the "Import Documents and settings from existing operation systems" step in the installer.

If I skip that step and tell it to go onto Install the base system it will do that and then error again back on the "Import documents..."

The error message says "The username you entered is invalid. Note that usernames must start with a lower-case letter, which can be followed by any combination of numbers an more lower-case letters"

The first time it happened I uninstalled it and tried a different username. It happened again.

I can' say it's the exact same problem as the previous user as he is using XP and I am using Vista Business.

Any idea how I get past this error? Thanks!

---

### Post by ago on 2007-06-22
can you check that the username is spelled correctly (with no upper case or nonalphanumeric char) in c:\wubi\install\preseed.cfg? Not that preseed.cfg is deleted as soon as you reboot, so you have to get that after a new installation and before reboot.

PS what is your locale and keyboard?

---

### Post by trelos on 2007-06-22
"can you check that the username is spelled correctly (with no upper case or nonalphanumeric char) in c:\wubi\install\preseed.cfg?"

it is correct in the preseed.cfg file

"PS what is your locale and keyboard?"

US / English

I suppose it probably has to do with Migration-assistant not supporting vista? ([https://bugs.launchpad.net/ubuntu/+source/migration-assistant/+bug/102094](https://bugs.launchpad.net/ubuntu/+source/migration-assistant/+bug/102094))

Is there anyway Wubi can skip that step optionally? I really could care less about it, especially if it will work otherwise.

---

### Post by ljk on 2007-06-22
> **ago said:**
> Yep you uninstall as any other app. When you uninstall a dialog comes up where you can select to back up the ISO so you do not have to redownload it when you reinstall

Great stuff! I'll try this when I get back to the office on Monday.

Many thanks & best regards.

---

### Post by macuser9214 on 2007-06-22
I downloaded WUBI and installed it, but no matter what username/password I try, I get: The username you entered is invalid.

It's all lowercase, no spaces...  I can't make it work for ANYTHING??

I need this done by tomorrow at the latest, so if someone can help, even a little, please do so.

Thanks.

---

### Post by chippy99 on 2007-06-22
When you installed WUBI it asked you to enter a username and password on the first page of the installation. Whatever you entered then is the username and password it is asking for.

---

### Post by macuser9214 on 2007-06-22
It's not asking me for anything. It's just saying that the username is invalid....

It's not giving me any options. If I press enter, it just flashes and give me the same error..

---

### Post by chippy99 on 2007-06-22
You should be seeing the Ubuntu login screen if the install was successful. There was a bug with capital letters in usernames causing an error like this. If you entered a username with capital letters try reinstalling and using a username that has all lowercase usernames.

---

### Post by ago on 2007-06-23
Ok when that happens can you guys please press Alt+F2 (that will give you a terminal)

Then copy /preseed.cfg and /var/log/syslog to /media/host/wubi:

cp /preseed.cfg /var/log/syslog /media/host/wubi

Then from windows zip preseed.cfg and syslog that you find in c:\wubi and attach it here. Thx

---

### Post by trelos on 2007-06-23
Here you go..

---

### Post by macuser9214 on 2007-06-23
[http://macuser9214.com/preseed.cfg](http://macuser9214.com/preseed.cfg)

[http://macuser9214.com/syslog](http://macuser9214.com/syslog)

those are my logs...

I've tried many usernames..   no luck.

please help!

---

### Post by ago on 2007-06-23
So please confirm the following:

* The username issue always appears towards the end of the installation (under mirgation-assistant setup, you should see something like "importing files and settings from other operating systems" just before that). Can you confirm that?

* I can see the same error in both cases:

ricky: Unable to open the registry file at '/media/host/Documents and Settings/ricky/NTUSER.DAT'
ricky, this means that you installed wubi in the same partition where you have windows, but we cannot access 

C:\Documents and Settings\ricky\NTUSER.DAT 

Any idea why? Is the file there (file path is case sensitive)? 

Trelos: Unable to open the registry file at '/mnt/migrationassistant/Documents and Settings/Trelos/NTUSER.DAT'
trelos, this means that you installed wubi on a different partition from the one where you have windows. Here again though we do not seem to be able to access: 

C:\Documents and Settings\Trelos\NTUSER.DAT 

Any idea why?

Do you have multiple XP installations? Is the profile on a different partition?

---

### Post by macuser9214 on 2007-06-23
The file is there, but in lower case.

If I change the case, will it break windows?

---

### Post by ago on 2007-06-23
> **macuser9214 said:**
> The file is there, but in lower case.

If I change the case, will it break windows?

Windows is not case sensitive but linux is. Give it a go.

---

### Post by macuser9214 on 2007-06-23
windows wouldn't let me change it..  I went to the linux install and used CP, to copy it with the new name, and it copied it, but the install still didn't work..

---

### Post by trelos on 2007-06-23
I mentioned previously my machine is a Vista one.. 

my ntuser.dat is located in

C:\Users\Trelos\ntuser.dat

ntuser.dat shows up lower case in windows.

---

### Post by macuser9214 on 2007-06-23
same as the above post..

---

### Post by ago on 2007-06-24
Do you have a folder called "C:\Document and Settings" or just "C:\Users"

In case try to copy "C:\Users\Trelos\ntuser.dat" -> "C:\Document and Settings\Trelos\NTUSER.DAT"

If you want to skip migration-assistant, before rebooting, edit c:\wubi\install\preseed.cfg and comment out the line:

d-i preseed/early_command string anna-install migration-assistant

---

### Post by trelos on 2007-06-24
There is no Document and Users folder

I'd rather just skip it.. I'd really it rather not migrate any Windows bookmarks etc anyways.

So I'll try that and see if that takes care of it.

---

### Post by macuser9214 on 2007-06-24
It won't work. I tried that already...

---

### Post by ChimpyFoo on 2007-06-24
hmmm same problem here but I didn't notice anything about NTUSER.DAT in my syslog, but hey here they are.

---

### Post by arsaha on 2007-06-25
Hello,

I too am facing the same problem. Whatever user name I try (with lowercase of course and no spaces, etc, etc), after the reboot, every time it stops after a couple of steps saying invalid username. I then have to abort the installation (pressing the esc key) and go back to windows and uninstall wubi.

I'm not installing wubi in my windows partition. I'm using a different partition on a single HDD on my laptop.
I have win XP home.
I selected a size of 8 GB for the installation, and the Kubuntu flavor.
I am using wubi-7.04.01

Let me know if you need any further information. Any help in this matter will be very much appreciated.

Thanks.

---

### Post by ago on 2007-06-25
Where exactly does it stop in your case, can you follow the instructions above and provide preseed.cfg and menu.lst.

It would also help if you edited c:\wubi\boot\grub appending "BOOT_DEBUG=2 debug=2" to the kernel line

---

### Post by ago on 2007-06-25
Can you guys confirm that you have the same issue even if you comment out the migration-assistant section in preseed.cfg?

---

### Post by trelos on 2007-06-25
I can can confirm I am still having an issue even if I comment the migration assistant section.

It gives me an error about cdrom media source or some such... I'll attach a new syslog with the exact message.

---

### Post by ago on 2007-06-25
Thx, please attach also the modified preseed.cfg, and specify your windows version, partition of windows, whether you have multiple windows installations and the partition where you installed Wubi.

---

### Post by Washizuka Keiichiro on 2007-06-25
I also have the same failure when i try install it. "User name error", then i deactivate the migration-assistant, and i have now the next error, "Failure load installer Component from CD" or some like that, i have just an XP service Pack 2, but i have tuneup utilities 2007. I give a virtual hard drive from 15 GB, and no numbers or upper case letters.

I just wanted to try Kubuntu.

---

### Post by ago on 2007-06-25
Press alt+f2 and then: nano /var/log/syslog or alt+f4

---

### Post by zero244 on 2007-06-25
Hey what is wubi, never heard of it.

---

### Post by ago on 2007-06-25
wubi-installer.org

---

### Post by Washizuka Keiichiro on 2007-06-25
I should Press alt+f2 when it give me the error? and then i console appears?, and i suppose to write *nano /var/log/syslog*? I never use linux before so i don't now that kind of linux basics.


Sorry for my English

---

### Post by Washizuka Keiichiro on 2007-06-25
I do what i thought to suppose to do... it send me to a kind of text editor when i get out whit alt+F4 

give me a list of dates and times, i saw this
Sed:"usr/share/migration-assistant/ma-script-utils"
then another that says "Loas-cdrom Failed"

I hope this be some helpful

---

### Post by ago on 2007-06-26
I'd need to know the exact error message for the lines that failed.

---

### Post by ljk on 2007-06-26
Greetings and many thanks to all who responded to my original post and subsequent replies.

First - I deleted Wubi but kept the backup files; downloaded a new Wubi; ran the installer but gave special attention to the detected user name.

Ago is absolutely right - the user name is definitely converted to lower case characters in the box on the installer.

On restart ->Ubuntu, the same process of "loading/installing/setting up etc."  began but the same "User Name"  problem occurred.

A warning box advised me that the user name was unacceptable and reminded me that only lower case letters/numbers could be used: this time I was sure that only lower case letters **_had _**been used.

Again,  the "Continue" button appeared but no amount of clicking on "Enter" or "Spacebar" could shift that warning box so, once more, I had to use the on/off button to switch off. [could this be a problem in the alternative i-386? Feisty release?]

I have used Wubi to install Ubuntu on 2 almost identical laptops. Both machines are part of the NEC "La Vie" range (sorry, I live in Japan & both PCs run Windows Japanese versions). My home laptop runs XP HOME and Wubi installed Ubuntu perfectly [the wireless difficulties I am having are a separate issue]. The work laptop runs XP Professional and that's the machine with the problems. 

Some differences are; the laptop with the problems has a red background when Ubuntu is being set up and you are asked to make various choices. The machine that had no problems had a blue background.
The problematic machine selects "drive D" to install onto by default - drive D has much more available space so I thought this was a good choice anyway. I haven't yet tried again using drive C. I will need to re-allocate space in order to do so. I was hoping Wubi would save me this task. The machine with no problems installed onto drive C.

When Ubuntu is selected as the start up OS  there are messages in the start up process (before any Ubuntu log in might be displayed) which I don't get in the "Wubi OK" machine. Most of these refer to errors in Windows - unfortunately I did not write these down and I do not know how to "screen shot" these things.

My hope is that Wubi gets even better - it has already given one of my machines a dual-boot ability without any difficult "Read The Manual" stuff or presenting me with choices I do not comprehend. What I can't understand is that I only get a little way into installing Ubuntu on a very similar machine when the "User Name" problem freezes everything.

Best regards to you all.

---

### Post by ago on 2007-06-26
> **ljk said:**
> Some differences are; the laptop with the problems has a red background
That is not normal, there might be an error that changed the installation process. I'd need to know at what stage it goes to the red screen and what messages you see in alt+f4. You might want to start the installer with the debug flags on as explained above.

> Most of these refer to errors in Windows - unfortunately I did not write these down and I do not know how to "screen shot" these things.
You can use a normal digital camera, then upload to imageshack or equivalent and post here the link

> What I can't understand is that I only get a little way into installing Ubuntu on a very similar machine when the "User Name" problem freezes everything.
I do not understand that either, but it is an error I cannot reproduce on my machine, therefore the only way for me to debug is to get a good error report from you guys. If you help me nail it down than I will try to fix it by next release.

---

### Post by Washizuka Keiichiro on 2007-06-26
Well i have this log:

Jun 26 13:46:02 main-menu [5313]: (process:6420):+
Jun 26 13:46:02 main-menu [5313]: (process:6420):read
Jun 26 13:46:02 main-menu [5313]: (process:6420): -r
Jun 26 13:46:02 main-menu [5313]: (process:6420):
Jun 26 13:46:02 main-menu [5313]: (process:6420):RET= k
Jun 26 13:46:02 main-menu [5313]: (process:6420):
Jun 26 13:46:02 main-menu [5313]: (process:6420):+
Jun 26 13:46:02 main-menu [5313]: (process:6420):return
Jun 26 13:46:02 main-menu [5313]: (process:6420): 0
Jun 26 13:46:02 main-menu [5313]: (process:6420):
Jun 26 13:46:02 main-menu [5313]: (process:6420):+
Jun 26 13:46:02 main-menu [5313]: (process:6420):return
Jun 26 13:46:02 main-menu [5313]: (process:6420):
Jun 26 13:46:02 main-menu [5313]: (process:6420):sed:
Jun 26 13:46:02 main-menu [5313]: (process:6420):/usr/share/migration-assistant/ma-script-utils
Jun 26 13:46:02 main-menu [5313]: (process:6420):no such file or directory
Jun 26 13:46:02 main-menu [5313]: WARNING **: configuring 'load-cdrom' failed with error code 1
Jun 26 13:46:02 main-menu [5313]: WARNING **: menu item 'load-cdrom' failed
Jun 26 13:46:31 init:startingpid 5260, console /dev/vc/2: 'binsh'

I apologize any mistake

---

### Post by ago on 2007-06-26
In preseed.cfg comment out all migration-assistant section EXCEPT the line that reads 

d-i preseed/early_command string anna-install migration-assistant

---

### Post by roachman5000 on 2007-06-26
I have a problem similar to the ones experienced in this thread.  I'm running Windows XP and tried to run Wubi to be able to dual-boot with Ubuntu.

The problem I get is the one where it is saying that I have an invalid user name.  I've used the default one selected by Wubi (firstname&lastname), and I've even tried other names as well, and I still get the error message regarding Invalid User Name.

Note:  When I tried using 'admin' as a login I got the red background mentioned earlier.

Please help!!!   For the record, I'm also a total N00b.

roachman5000

---

### Post by Washizuka Keiichiro on 2007-06-26
Thanks ago that work, i can run ubuntu, but a cuestion where i cand find help for change resolution of the screen and config the audio?

Thanks again

---

### Post by ago on 2007-06-27
> **Washizuka Keiichiro said:**
> Thanks ago that work, i can run ubuntu, but a cuestion where i cand find help for change resolution of the screen and config the audio?

Thanks again

Thank you,

You were very helpful in pinpointing the problem, I'll get it fixed by next release.

Washizuka now that you have Ubuntu running you should use the general Ubuntu support forum for any issue/question, we have done our part ;)

---

### Post by san425 on 2007-06-27
[http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)
:(

Another "HEEELP" I've been trying to get Wubi to install Ubunto for the last 6 hrs or so. I downloaded the Wubi installer and the iso from the links on the wubi page today 27/June twice to make sure the first lot wasn't faulty. I keep coming up against the "invalid username" problem, despite working through the various solutions offered in this and other threads. (That's what took so much time. I'm a rank amature at this software tinkering)  I'm about ready to give up. I gather I'm not the only one experiencing problems.

My machine is an old Toshiba Satellite Pro 4300, P11 500, 256mb ram, 40 gb hd devided into a 10 gb c:\ drive housing win xp pro and a 30gb partition where wubi tried to put Ubuntu. I understand Ubuntu may run slower than desirable, but I'm willing to give it a go. Win xp has been running fine for the jobs I need it to do.

Any help or advice would be welcomed with open arms. Thank you.

[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)
:)

---

### Post by san425 on 2007-06-27
:)
 Umm.... even getting the smilies right is straining the brain at the moment
:)

---

### Post by macuser9214 on 2007-06-27
How do you comment those lines out before you copy it to /media/host or whatever?

Because if I do it after that, and restart, it will give me an error about the install not being complete, so, Where does it install preseed.cfg BEFORE I cp it to the wubi direcotry, so i can edit THAT file?

---

### Post by ago on 2007-06-27
The solution is:

1) Do a fresh installation of Wubi-7.04.01. Do NOT reboot.
2) Edit the file c:\wubi\install\preseed.cfg
3) Comment (use "#") all the migration-assistant section, EXCEPT the line 

"d-i preseed/early_command string anna-install migration-assistant"

4) Save and reboot
5) Let me know if it works or not

---

### Post by roachman5000 on 2007-06-27
That did the trick for me!

It works just fine now, thanks a million!

Now I just have to get it to recognize my wireless driver, but that's a whole different battle....

---

### Post by macuser9214 on 2007-06-28
worked fine for me too, but ubuntu doesn't install with ndiswrapper, so I have to wait till I get home to install the wireless stuff.

I'll probably do it tomorrow.

---

### Post by viralbug on 2007-06-28
that worked for me too!
everything worked perfectly! :)

---

### Post by macuser9214 on 2007-06-29
WARNING THOUGH:::

Do not turn off the computer while it's starting up. You will lose your WINDOWS AND LINUX systems.

Currently I can't boot to either :(

---

### Post by ljk on 2007-07-02
> **ago said:**
> The solution is:

1) Do a fresh installation of Wubi-7.04.01. Do NOT reboot.
2) Edit the file c:\wubi\install\preseed.cfg
3) Comment (use "#") all the migration-assistant section, EXCEPT the line 

"d-i preseed/early_command string anna-install migration-assistant"

4) Save and reboot
5) Let me know if it works or not

Yes! Thank you very much indeed.

---

### Post by ago on 2007-07-04
Can you please try [http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04.217.64.exe](http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04.217.64.exe) and let me know if it works or not?

---

### Post by Starks on 2007-07-04
> **ago said:**
> Can you please try [http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04.217.64.exe](http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04.217.64.exe) and let me know if it works or not?
Still not fixed...

"Invalid username" is now "Empty password".

---

### Post by ago on 2007-07-04
second try
[http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield-217.65.exe](http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield-217.65.exe)

---

### Post by kifcaliph on 2007-07-05
well it works great ......but there is another thing that I cant finalize the installion

---

### Post by ago on 2007-07-05
> **kifcaliph said:**
> well it works great ......but there is another thing that I cant finalize the installion

can you send me the file /var/log/syslog?

---

### Post by kifcaliph on 2007-07-05
> **ago said:**
> can you send me the file /var/log/syslog?

how can I get the file /var/log/syslog 

well it shows me "finishing installation" and then go to "Ubuntu installaion menu"...  it doesn't reboot or even start Ubunto.

---

### Post by ago on 2007-07-05
You can press alt+f2, then copy the log to the windows drive:

cp /var/log/syslog /media/host

you will then find syslog under C:\, zip it, and attach to the post here.

Thx

---

### Post by kifcaliph on 2007-07-05
I need more details

I reinstalled it.....and ran the command cp /var/log/syslog/media/host then restart the pc and I didn't find anything in C:/ except windows xp files and folders

---

### Post by ago on 2007-07-05
> **kifcaliph said:**
> I need more details

I reinstalled it.....and ran the command cp /var/log/syslog/media/host then restart the pc and I didn't find anything in C:/ except windows xp files and folders

Watch the spaces

cp [space] /var/log/syslog [space] /media/host

it's like windows: copy source destination

---

### Post by kifcaliph on 2007-07-05
here is what I've found

[files%20in%20C%20directory.zip]("http://www.freespaces.com/kiflab/files%20in%20C%20directory.zip")

[logs%20in%20wubi%20folder.zip]("http://www.freespaces.com/kiflab/logs%20in%20wubi%20folder.zip")

[preseed.cfg.tmplate.zip]("http://www.freespaces.com/kiflab/preseed.cfg.tmplate.zip")

---

### Post by ago on 2007-07-05
I cannot access the links can you simply attach the zipped version of syslog here?

---

### Post by kifcaliph on 2007-07-05
here they are

---

### Post by ago on 2007-07-05
hmm l'unico file che mi serve manca: syslog. Come spiegato, una volta che ti blocchi premi alt+f2 e poi copialo su /media/host

---

### Post by kifcaliph on 2007-07-05
I am sorry but I did find any of "syslogs", 
however I ran the command cp [space]/var/log/syslog/ [space]/media/host ... it makes no sign to show me any thing.. and it didn't tell me that the command is wrong.....it justs show me the #

---

### Post by ago on 2007-07-05
it's 
```

cp    /var/log/syslog     /media/host

```

---

### Post by kifcaliph on 2007-07-05
hey I am not fool ... I know wat is the [space] mean.... I did it as you mentioned but there is nothin in my C: drive

---

### Post by ago on 2007-07-05
check with 

ls /var/log
cp /var/log/syslog /media/host
ls /media/host

(it's a lower case "LS")

note that you have to copy after a fresh install

---

### Post by kifcaliph on 2007-07-05
here it is ...

---

### Post by kifcaliph on 2007-07-05
> **ago said:**
> Do you have multiple XP installations? Is the profile on a different partition?

this is your question to terlos ....I am also have multiple installions.

---

### Post by ago on 2007-07-06
thanks, I'll have a look later on today

---

### Post by ago on 2007-07-08
Can you pls try [http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield-223.72.exe](http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield-223.72.exe) ?

---

### Post by ago on 2007-07-09
I need some feedback here so please try it out if you had the invalid username problem

---

### Post by sarahlizz3 on 2007-07-09
I am also having this same problem.  I attempted this [http://cutlersoftware.com/ubuntusetu...eld-223.72.exe](http://cutlersoftware.com/ubuntusetu...eld-223.72.exe) install to give you some feedback.  I have also tried several user IDs and several installs at this point.  The only thing I have not done is change that file that was mentioned earlier, I thought I would try this first so you knew if it worked.

It ran through the install on windows, rebooted began to finish the install after reboot and then just went to black screen.  I have attempted this twice, unfortunently I cannot tell you exactly where it stopped as both times I happened to look away from my laptop right before it stopped - and I don't think I can bear to go through it again right now waiting for the line it failed on.  (I can tell you it was a couple lines after it was looking for RAID devices).  

I'm on a Toshiba Satellite laptop, running XP Media Center 2005 
Intel T2050 - both 1.6 GHz
1 GB RAM
Don't know if there is anything you need to know about my system 

Also, I know virtually nothing about Linux - just to give an idea of where i'm at technically.

---

### Post by ago on 2007-07-09
> **sarahlizz3 said:**
> It ran through the install on windows, rebooted began to finish the install after reboot and then just went to black screen.

That might be a completely different issue (possibly due to missing video driver). If I understand it correctly, it did finish the installation and reboot. On the second reboot did you see the ubuntu logo?

---

### Post by sarahlizz3 on 2007-07-09
No, it did not get that far.  When I say it was starting the install after reboot, it was still in the booting up process (possibly still determining the hardware on system) so I may be inaccurate in saying that it was installing at the moment that it went to black screen, it was probably still in boot up process.  

I just did a fresh install of original install and commented out those lines.  I am  rebooting right now, and will let you know what happens with this attempt.  Its been sitting at the following for awhile though:

Loading, please wait...
No RAID disks

---

### Post by sarahlizz3 on 2007-07-09
Ok, here's where it is stuck at this time:

No RAID disks
Check root = bootarg cat /proc/cmdline
Or missing modules, devices cat/proc /modules ls/dev
Alert! does not exist. Dropping to a shell!

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)

/bin/sh: can&#8217;t access tty; job control turned off
(initramfs)

(also - I believe this is what it said before it went to black screen before)

Edit:  It did go to a black screen again after a couple of minutes at being stuck at the above.

---

### Post by ago on 2007-07-09
Usually that is either due to the windows partition not being "clean" (you have to use chkdisk /f from windows and defragment) and/or to the use of unsupproted raid. You'd need to provide me the files in /tmp/zenigata.log and /tmp/lupin.log to find out for sure. But it does not seem to be related to the username issue.

---

### Post by sarahlizz3 on 2007-07-09
The user name error (same as everyone else) was what I was receiving before I tried the following install: [http://cutlersoftware.com/ubuntusetu...eld-223.72.exe](http://cutlersoftware.com/ubuntusetu...eld-223.72.exe) 

I had attempted about 5 installs (changing user names, etc.) and every time was recieving the invalid user name, name must be all lower case...  error message

After attempting that install is when I started having the other problem.

---

### Post by kifcaliph on 2007-07-09
Hi Ago
thank you Ago …….Well it works great for me using [http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield-223.72.exe]("http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield-223.72.exe")
it finished the installation with no errors…thank you again ago

---

### Post by sarahlizz3 on 2007-07-10
Ok I tried again today after making sure to delete every trace of the first few attempts, and that last link did work for me.  Thanks!

---

### Post by Starks on 2007-07-13
Install works flawlessly, but every time I start Ubuntu, it bugs out at the login screen.

1. Looping sounds.
2. Slow mouse (touchpad is fine).

---

### Post by LunixRoks123 on 2007-07-25
Thats wierd
:confused:

---

### Post by jstaryuk on 2007-10-20
So I install Ubuntu and when I reboot and choose to boot into ubuntu, it goes and loads, but then it pops up with "Invalid user name." I thought I used a lower-case name, but I decided to reinstal anyway just to be sure. 

So I reinstall, this time making SURE it was lower-case. I boot up, and it gives me the same message. I reinstalled AGAIN and the same thing happened. How can I fix this?! :confused: Please help!

---

### Post by ago on 2007-10-20
> **jstaryuk said:**
> So I install Ubuntu and when I reboot and choose to boot into ubuntu, it goes and loads, but then it pops up with "Invalid user name." I thought I used a lower-case name, but I decided to reinstal anyway just to be sure. 

So I reinstall, this time making SURE it was lower-case. I boot up, and it gives me the same message. I reinstalled AGAIN and the same thing happened. How can I fix this?! :confused: Please help!
Did you use 7.04.04?

---

### Post by cheetex on 2010-03-17
Hi,
I installed Ubuntu using an iso copied onto a formatted thumb drive (I used UNetbootin). It starts up fine, and i can complete the first 4 steps of the installation (location, keyboard, hard drive formatting) but when i get to the screen titled "who are you", it gives me an error message saying that my username is invalid. I cannot close this error message, and i cannot stop the installation. The only way to stop it was to shut down.
Any help would be greatly appreciated.

P.S.: My computer runs XP home

---

