---
title: "Armitage problem, please help!"
date: 2018-05-05
forum: General Help
---

### Post by winter-is-coming on 2018-05-05
Hello,


I am new to Linux, to command prompts/terminal and also new to this forum.  I consider myself to have average computer knowledge for someone my age (34) being that I grew up in the age of the internet.  I am by no means "advanced" in any area of computing, but I can usually diagnose my own issues, setup my home network, and all the typical things a typical person my age can do.  I recently have grown a passion for learning more about computers (i know saying "learning about computers" is broad and ambiguous but I want to learn about everything, networking, programming, security, etc...).  I recently deleted windows from this computer and installed Ubuntu.  So far I am really liking it and it seems just as user friendly as my other computer which is a mac.  Anyway, enough about me, I'm here for a reason.  Now before I get into what my problem is let me say that this is not my first rodeo when it comes to forums.  I've been members of many forums and BBC's throughout my life on all different topics and I know the general rules and policies to expect.  I know people HATE when someone asks a question without doing any research first.   I know people HATE when someone asks a question that has already been asked on that forum.  Coincidentally, I am the type of guy who HATES to have to ask someone to solve my problem.  I like to figure things out on my own and only as an absolute last resort do I ask.  Now, I have spent the past 3 days of non-stop research, googling, watching videos, lurking on forums, and of course I searched this entire forum.  No doubt the question I am asking some of you will think has already been asked on this forum (which it has) yet if you read my whole post you will see why I am still posting it.  I am having "initially" the same problem it may seem as others, but I have actually done pretty much EVERYTHING I can do to solve this that my limited knowledge allows and abundance of research has brought me to.  Therefore I graciously ask you to read on and not flame me.  Please remember my knowledge is limited and so what may seem like an obvious answer to you, may not be to me.  So enough talk, here is my problem:


I have installed Metasploit and it works no problem.  I installed PostgreSQL and that seems to be working no problem.  However, I am now trying to install Armitage and that is where the problem lies.  I was able to download and extract the files into my downloads folder. To start running the program in terminal I have to go to the directory where its located (/home/Downloads/armitage) and in the command-prompt type: [COLOR=#0000ff]*./armitage*[/COLOR] which starts the program, and it starts just fine.  The first thing that happens is a window pops up asking me to click "CONNECT" which is normal and supposed to happen. However when I click "CONNECT" it brings me to this next window which is not supposed to happen:


[IMG]https://i.imgur.com/kKS4LFB.png[/IMG]


Now right now I bet is when you're all saying to yourself "Omg, we have been asked this a million times, google has been asked it a million times" but I say to you, please hear me out!  Now from this point on, in the rest of this post I'm going to refer to this window above as "The Problem Window" just to make things easier and faster.  Being that I'm not a computer expert but being that I do know how to read, i deduced from the first sentence on this Problem Window that Armitage apparently can't find a file called "*[COLOR=#0000ff]database.yml[/COLOR]*".  That much is clear.  Then, it gives me three options to try and help me diagnose.


**1**. **"Try setting MSF_DATABASE_CONFIG to a file that exists**" : well I'll tell you right now, i had no idea what that meant. I didn't even know what **MSF_DATABASE_CONFIG **was.  Although I can deduce MSF is probably short for Metasploit-Framework because i have heard that term being said in my research.  I also deduced that because in order to start Metasploit in terminal I have to type "msfconsole".  So through my powers of deduction I came to realize MSF stands for Metasploit-Framework.  Now the next word DATABASE is pretty self explanatory.  The last word "CONFIG" obviously is short for configure.  However just because i know what each individual term might mean, i still have no idea what **MSF_DATABASE_CONFIG** is and what 'file' it is supposed to be 'set' to.  


**2.** **Did you use sudo to start this program? Try [COLOR=#0000ff]sudo -E[/COLOR]** :  Ok well this option I can at least understand and try.  Since I have been learning about the command prompt (both on this Linux machine and my mac) I have become familiar with some of the commands.  I know 'sudo' stands for Super User Do and is basically giving me admin/root like privileges temporarily.  I looked up what the -E means and I didn't really understand it.  It had something to do with environments but again, I'm still dumb with computes so I didn't get.  Regardless of me understanding it or not I still knew I could try this option (more on this in a minute)


**3.  Kali Linux 1.Xusers, try this:**
     [COLOR=#0000ff]service metasploit start
     service metasploit stop[/COLOR]


    **Kali Linux 2.X users, try this:**


    [COLOR=#0000ff]msfdb init[/COLOR]


Ok well since I don't have Kali Linux, I have Ubuntu, I didn't bother reading or trying to understand this option (at first).  However throughout my research the last few days I did come to understand that most Linux distro's still use the same command-prompts (for the most part, right?) and that reading something about my particular issue on a site dedicated to talking about Kali could indeed be helpful still.  For now though, lets stick to what I did in chronological order.


So the The Problem Window gave me three options to try.  Naturally, the only one I understood and could even try was option 2.  So I entered the following command:
[COLOR=#0000ff]sudo -E ./armitage[/COLOR] but instead of starting up like it did the first time with a window popping up asking me to connect, it just stayed in terminal, a bunch of text scrolled down the screen.  For the sake of being thorough this is what I got in the terminal window after typing [COLOR=#0000ff]sudo -E ./armitage:
[/COLOR]

[FONT=courier new]No protocol specified[/FONT]
[FONT=courier new]Exception in thread "main" java.awt.AWTError: Can't connect to X11 window server using ':0' as the value of the DISPLAY variable.[/FONT]
[FONT=courier new]    at java.desktop/sun.awt.X11GraphicsEnvironment.initDisplay(Native Method)[/FONT]
[FONT=courier new]    at java.desktop/sun.awt.X11GraphicsEnvironment.access$200(Unknown Source)[/FONT]
[FONT=courier new]    at java.desktop/sun.awt.X11GraphicsEnvironment$1.run(Unknown Source)[/FONT]
[FONT=courier new]    at java.base/java.security.AccessController.doPrivileged(Native Method)[/FONT]
[FONT=courier new]    at java.desktop/sun.awt.X11GraphicsEnvironment.<clinit>(Unknown Source)[/FONT]
[FONT=courier new]    at java.base/java.lang.Class.forName0(Native Method)[/FONT]
[FONT=courier new]    at java.base/java.lang.Class.forName(Unknown Source)[/FONT]
[FONT=courier new]    at java.desktop/java.awt.GraphicsEnvironment$LocalGE.createGE(Unknown Source)[/FONT]
[FONT=courier new]    at java.desktop/java.awt.GraphicsEnvironment$LocalGE.<clinit>(Unknown Source)[/FONT]
[FONT=courier new]    at java.desktop/java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(Unknown Source)[/FONT]
[FONT=courier new]    at java.desktop/sun.awt.X11.XToolkit.<clinit>(Unknown Source)[/FONT]
[FONT=courier new]    at java.base/java.lang.Class.forName0(Native Method)[/FONT]
[FONT=courier new]    at java.base/java.lang.Class.forName(Unknown Source)[/FONT]
[FONT=courier new]    at java.desktop/java.awt.Toolkit$2.run(Unknown Source)[/FONT]
[FONT=courier new]    at java.desktop/java.awt.Toolkit$2.run(Unknown Source)[/FONT]
[FONT=courier new]    at java.base/java.security.AccessController.doPrivileged(Native Method)[/FONT]
[FONT=courier new]    at java.desktop/java.awt.Toolkit.getDefaultToolkit(Unknown Source)[/FONT]
[FONT=courier new]    at java.desktop/sun.swing.SwingUtilities2.getSystemMnemonicKeyMask(Unknown Source)[/FONT]
[FONT=courier new]    at java.desktop/javax.swing.plaf.basic.BasicLookAndFeel.initComponentDefaults(Unknown Source)[/FONT]
[FONT=courier new]    at java.desktop/javax.swing.plaf.metal.MetalLookAndFeel.initComponentDefaults(Unknown Source)[/FONT]
[FONT=courier new]    at java.desktop/javax.swing.plaf.basic.BasicLookAndFeel.getDefaults(Unknown Source)[/FONT]
[FONT=courier new]    at java.desktop/javax.swing.plaf.metal.MetalLookAndFeel.getDefaults(Unknown Source)[/FONT]
[FONT=courier new]    at java.desktop/javax.swing.UIManager.setLookAndFeel(Unknown Source)[/FONT]
[FONT=courier new]    at java.desktop/javax.swing.UIManager.setLookAndFeel(Unknown Source)[/FONT]
[FONT=courier new]    at java.desktop/javax.swing.UIManager.initializeDefaultLAF(Unknown Source)[/FONT]
[FONT=courier new]    at java.desktop/javax.swing.UIManager.initialize(Unknown Source)[/FONT]
[FONT=courier new]    at java.desktop/javax.swing.UIManager.maybeInitialize(Unknown Source)[/FONT]
[FONT=courier new]    at java.desktop/javax.swing.UIManager.getInstalledLookAndFeels(Unknown Source)[/FONT]
[FONT=courier new]    at ui.MultiFrame.setupLookAndFeel(MultiFrame.java:158)[/FONT]
[FONT=courier new]    at armitage.ArmitageMain.main(ArmitageMain.java:199)[/FONT]


Right, so this is what I got after trying option 2 from The Problem Window and clearly didn't help.  So my next thought was to go to Armitage's website and find their troubleshooting page. Sure enough I scroll down the page and find this very issue mentioned on the troubleshooting page. I was so hopeful at that point.  Here is what the said:


[IMG]https://i.imgur.com/eAJNqnu.png[/IMG]


Look at that.  The title of this troubleshooting section is exactly what was written on top of The Problem Window: "**I cannot find the database.yml. I *really* need it**_"_.  I thought I'd be gold since they recognize that this must be a common enough problem if it's on their troubleshooting page.  Well unfortunately for me, this wasn't all that much more helpful than the info provided in The Problem Window itself.  Only slightly more helpful.  It did clear a few things up though.  So this web page starts by saying "To connect to the Metasploit Framework Database, Armitage needs to know the location of [COLOR=#0000ff]database.yml[/COLOR] file.  This is normally available in the **MSF_DATABASE_CONFIG** environment variable."  Ok well from the info provided from The Problem Window alone I already knew there was a file called [COLOR=#0000ff]database.yml[/COLOR] that was missing and this just kind of re-iterates that, though it does add a little bit more saying it needs to know it's "location" so this got me thinking "well maybe I do have it but it's not in the place it needs to be".  I don't know, just a stupid guess cause I know nothing.  Then it said it was normally in the "**MSF_DATABASE_CONFIG **environment variable.  Well ok, before I had no idea what **MSF_DATABASE_CONFIG **even was (and I still don't); and The Problem Window said that I should try setting **"MSF_DATABASE_CONFIG**" to a file that exists.  Remember I didn't know what "file" they wanted me to set it to? Well now at least I know they did mean to "set" **MSF_DATABASE_CONFIG** to [COLOR=#0000ff]database.yml[/COLOR].  Yay! Well actually its not time to celebrate yet cause I still have no idea how to "set" a file to a thing called** MSF_DATABASE_CONFIG** because i still don't know what the hell a **MSF_DATABASE_CONFIG** is.... nor do I know how to "set" a file to a "THING_SOMETHING".  


Ok so the next thing it tells me in this troubleshooting is that if I installed Metasploit by hand to make sure  MSF_DATABASE_CONFIG is set.  Well, I didn't install it by hand, and even if I did... i still don't know what "set" is.  Sorry, you guys must think I'm sooooo dumb... which I am with computers.  I'm a beast on the guitar though I swear.  Anyhow, it then continues on to repeat the same instructions from The Problem Window, and that is to try[COLOR=#0000ff] sudo -E, [/COLOR]but we already know that[COLOR=#0000ff][/COLOR] didn't work.  After telling me to try [COLOR=#0000ff]sudo -E[/COLOR] again, it then goes on to explain why it might work.  I don't really understand the explanation but I do kind of understand.  Since I already know that "sudo" command temporarily puts the user in the "root" state for whatever command follows;  apparently it's saying that this command (in my case [COLOR=#0000ff]./armitage[/COLOR]) following [COLOR=#0000ff]sudo[/COLOR] will inherit the environment that is normally the environment when a user is in "root".  Which apparently affects **MSF_DATABASE_CONFIG**?  Yet I still don't get really any of it.. just some things I'm deducing.


Lastly, this troubleshooting guide tells Kali Linux users to try:
[COLOR=#0000ff]service postgresql start
service metasploit start
service metasploit stop[/COLOR]


Well at this point I thought "what the hell", let me try these commands it is telling the Kali Linux users to try.  I'll also let you know that later on in the days of my research, I did keep reading about these commands so I would have eventually tried them anyways.  


Here is what happens when I enter "[COLOR=#0000ff]service postgresql start[/COLOR]": It pops up a window asking for a password for Authentication and then just brings me right back to the command prompt without any errors.  It just returns me to the command prompt right underneath the command I typed above. 

So because of my ignorance on this subject, to me it seems as if nothing happened.  I typed in the command [COLOR=#0000ff]"service postgresql star[/COLOR]t" and pressed enter which brought me to an Authentication screen where it required my password.  Once I type the password in and hit "Authenticate" it just brings me right back to terminal like nothing happened.  Now I assume something is running in the background but I don't know what.

So after doing this I tried to start Armitage and still get The Problem Window. 

Naturally, I tried the next two commands on the troubleshooting page for Kali users (which if you remember were also suggested on the original Problem Window for Kali uses):
[COLOR=#0000ff]service metasploit start
service metasploit stop
[/COLOR]
So when I try to enter the first command: [COLOR=#0000ff]service metasploit start,[/COLOR] here is what happens:  It once again pops up a window wanting a password for Authentication.  I enter the password and click authenticate but then brings me back to terminal with this error:



[IMG]https://i.imgur.com/Z6WRckV.png[/IMG]


So as you can see that didn't work.  After I typed the command [COLOR=#0000ff]service metasploit start[/COLOR] it brought me to an Authentication window again.  I enter my password and hit "Authenticate" and it brings me back to the terminal but with and error message this time saying "**Failed to start Metasploit.service: Unit Metasploit.service not found**". So obviously you can imagine from what you've read about me so far, that I have no idea what this means.  The weird part is, Metasploit, the actual program, works!  When I run it, by typing [COLOR=#0000ff]msfconsole[/COLOR], it starts up perfectly and no problems. Anyway, needless to say I did not try the third command on that list since it was [COLOR=#0000ff]service metasploit **stop**[/COLOR].  Obviously there was nothing to "stop" since I couldn't get the first command to "start".


Ok so the Armitage website got me nowhere.  Now onto my independent research.  I am not going to give you guys every little thing I did because this post is already going to be long enough, plus i couldn't possibly remember all it, but here are the highlights from what else I tried.


1.  I heard that maybe PostgreSQL wasn't connected so I followed some instructions and when I type in this command: [COLOR=#0000ff]sudo -u postgres psql postgres[/COLOR] this is what happens:






[IMG]https://i.imgur.com/ZdakAJM.png[/IMG]




Now I have no idea what PSQL is, since I already told you earlier I'm shaky on the concept of postgreSQL that I downloaded, it's no wonder I don't know what PSQL is...but apparently it's related to postgreSQL, and whatever it is I did in the pictures above clearly worked and let me "log in" if you will.  


Ok so after some more research I was told to check the status of a connection with Metasploit and postgresql.  So I ran Metasploit and once Metasploit starts I was told to type in "[COLOR=#0000ff]db_status[/COLOR]".  I'll just let the rest of the pictures do the talking, you can follow along what is happening. 


-So I start up Metasploit
-It loads up all good and well, no problems
-In Metasploit the prompt changes to _msf>_.  So now I type in "[COLOR=#0000ff]db_status[/COLOR]"
-And as you can see everything looks good. It says postgreSQL is connected to MSF


[IMG]https://i.imgur.com/aGKnm9D.png[/IMG]



So I exit out of Metasploit.  Now what?  Well like any good pioneer would do.. on with the research.  Well in my research I heard someone say to type this command in to see what it says "[COLOR=#0000ff]*msfdb init*[/COLOR]" which if you remember it was also one of the suggestions for Kali users on the original Problem Window.  [SIZE=1]**By the way, I forgot to mention. I try to start Armitage after every change or after trying every one of these things I've listed above.  Obviously it still doesn't work since I'm still telling you about the problem, but just so you know, any little change I make, I try Armitage right after and everytime I still get that damn Problem Window.  *[SIZE=2]So this is what happens when I type "[COLOR=#0000ff]*msfdb ini*[/COLOR]t", take a look:

[/SIZE][/SIZE]


[IMG]https://i.imgur.com/ahnJDSH.png[/IMG]

Now this was really interesting to me.  At first looking at the result it meant nothing.  However I could clearly read that it said a "_database_" was found at this path [COLOR=#0000ff]**/home/joe/.msf4/db**[/COLOR].  And since the whole issue I'm having is getting past this Problem Window that states it is missing a file called [COLOR=#0000ff]"***database.yml***[/COLOR]" i thought there might be a connection so I followed the path that is printed on the screen.  However in my [COLOR=#0000ff]**/home/joe/**[/COLOR] path there is no folder named "[COLOR=#0000ff]**.msf4**[/COLOR]".   Ah, but then I remembered about hidden files so I looked for hidden files and sure enough there she was.  I open up** .msf4** and what do you know? Inside is a file called "[COLOR=#0000ff]***database.yml***[/COLOR]"     BINGO!   I got excited.  Too bad that excitement slowly turned to defeat when I realized that I don't know anything about computers and just cause I located this file doesn't mean I know what to do with it.  Oh, I bet some of you at this point are saying "why didn't you just do a simple search for a file called "[COLOR=#0000ff]*database.ym*l[/COLOR]" or even a search for any file ending in "*.[COLOR=#0000ff]yml[/COLOR]*"?  Well for your information I did, i forgot to mention it earlier.  I swear when I did the search the first few times a couple days ago the file didn't show up, however now when I do it, I do see it.  What was strange though was when I did the search the first couple times (by using "*[COLOR=#0000ff]locate -i "*.yml[/COLOR]*") the results only returned like 6 or 7 files and none of them were "*[COLOR=#0000ff]database.yml[/COLOR]*".   However, _now_ when I do the same search, or if I just search for the actual file name ([COLOR=#0000ff]*locate "database.yml*[/COLOR]) it returns a HUGE list of sooooo many files with[COLOR=#0000ff]** /home/joe/.msf4/datbase.yml **[/COLOR]as the first result.  I swear I'm not crazy.  Something I did in the process must have had an affect on the search results.  Anyway, that's neither here nor there, the fact is I located *[COLOR=#0000ff]"database.yml[/COLOR]*".  Now the question is how to I "set" it to that** MSF_DATABASE_CONFIG** thing?


This may be unrelated (sorry if I'm all over the place and hard to follow) but I also read that I should enter this command to see what happens: [COLOR=#0000ff] /etc/init.d/postgresql start[/COLOR]
So I did and here are the results of what happened:


[IMG]https://i.imgur.com/v8g9XrK.png[/IMG]

God, I would love to know what all this means but that is why im learning as much as I could.  Anyway, I'm not sure that that has to do with anything. I mean, again, i can read so i see the word *[COLOR=#0000ff]"postgresql[/COLOR]*" in there which I know is that SQL program I installed.  I also see it says "*[COLOR=#0000ff]postgresql.service[/COLOR]*" which I'm sure is connected to earlier when I had to type the command "*[COLOR=#0000ff]service postgresql start[/COLOR]*"; but just because I'm recognizing things doesn't mean I understand.  

Ok,  so the last thing I will tell you that I attempted.  In my searching I found someone asking the very question I am asking.  Here is the guys question I found on some Linux Mint forum and some other guys response.  For sake of ease lets call the guy with the same problem as me who is asking the question "Hopkins" and the guy who is making suggestions "Helper".  Here is Hopkins question :
*"[COLOR=#333333][FONT=&amp]In the process of installing armitage on Linux Mint 18.2 I am stuck on an error message. I run ./armitage through root user I need to set a MSF_DATABASE_CONFIG environment variable that stores a database.yml file. How can I set this variable and route it to the database.yml file?[/FONT][/COLOR]*

Here is what the Helpers response was:
[COLOR=#800000]
[FONT=&amp]In the terminal enter [/FONT]MSF_DATABASE_CONFIG=whatever_it_needs_to_be
[FONT=&amp]To check it [/FONT]echo $MSF_DATABASE_CONFIG

[FONT=&amp]Example
[/FONT][FONT=Monaco][bill@XPS] ~ $ MSF_DATABASE_CONFIG=whatever_it_needs_to_be
[bill@XPS] ~ $ echo $MSF_DATABASE_CONFIGwhatever_it_needs_to_be
[bill@XPS] ~ $ [/FONT][/COLOR][COLOR=#2E8B57][FONT=Monaco]
[/FONT][/COLOR]
So I tried doing what this guy suggested.  In terminal I typed "[COLOR=#0000ff]MSF_DATABASE_CONFIG=database.ym[/COLOR]l"  
but I wasn't sure if this was correct.  I wasn't sure if i was supposed to just put **=database.ym**l or put the whole path like** = /home/joe/.msf4/database.yml**
Again i should know but I am dumb

So I tried doing it the first way (without the full path)

As you can see after i typed it in and hit enter there were no errors so I thought maybe it worked.  So I tried the guys suggested next command which he says was "to check it" so I typed:
"[COLOR=#0000ff]echo $MSF_DATABASE_CONFIG[/COLOR]" and it returned a result saying it was tied to "[COLOR=#0000ff]*database.yml*[/COLOR]" which i thought was a good thing, see:

[IMG]https://i.imgur.com/QLu7GtH.png[/IMG]

But that didn't solve the problem.  If I try to start Armitage I still get the Problem Window.  By the way here is a link to this other forum i'm referring to.  It's easier for you guys to read it (its very short) rather than me keep typing each of their responses back and forth: [https://forums.linuxmint.com/viewtopic.php?t=258816](https://forums.linuxmint.com/viewtopic.php?t=258816)

Since this didn't work for me or for Hopkins, the Helper's next suggestion was this:
[COLOR=#333333][FONT=&amp]"[/FONT][/COLOR][COLOR=#a52a2a][FONT=&amp]If you don't have a ~/.bashrc, create it and add[/FONT][/COLOR]export MSF_DATABASE_CONFIG=whatever_it_needs_to_be[COLOR=#a52a2a][FONT=&amp] or if you already have one just add that line.[/FONT][/COLOR][COLOR=#333333][FONT=&amp]"

[/FONT][/COLOR]Omg!! This guys response right here was the one that almost made me lose my mind. I spend about 7 hours non-stop researching.  First of all i have no idea what a** .bashrc **file is.  Second I didn't know what he meant to "**export MSF_DATABASE_CONFIG=(still not sure if this should be the whole path or just '*database.yml*'**), and lastly I don't know what he means "just add that line".

Holy cow it took me forever but I finally figured it out.  I found out where this** .bashrc** file is. I already had one so I did not have to create it.  I finally realized I could open it in Gedit so it opened as a text file.  Then it made sense when he said "just add that line" since I knew it as a text file.  Still though I have a lot of questions and things I don't understand.  First, there are like 10 "**.bashrc**" files on my computer, all in different locations.  So which one do I add that "line of text" to?  Hopkins  is having the same problem as me.  He did a search and also had a bunch of **.bashrc** files but for some reason he didn't have one in his HOME directory, but I did.  The Helper suggested he copied the "**.bashrc**" file from **/etc/skel/ **folder and put the copy in his HOME folder.  I didn't think I needed to do this since I already had a** .bashrc** file in my HOME folder, right?  Second, so the Helper is telling us to put  [COLOR=#2E8B57][FONT=monospace]export MSF_DATABASE_CONFIG=whatever_it_needs_to_be [/FONT][/COLOR]into that **.bashrc** file, but as I said before the part where he wrote "whatever_it_needs_to_be" I'm not sure what to replace it with? Do I replace it with the full path to "***database.yml***" like this:
[COLOR=#0000ff]export MSF_DATABASE_CONFIG=/home/joe/.msf4/database.yml[/COLOR]

or do I do it like this:
[COLOR=#0000ff]export MSF_DATABASE_CONFIG=database.yml

[/COLOR]I went on a limb and assumed I had to open the .bashrc file that was located in my home folder.  So i opened that and added at the very bottom of the page both versions of what I just typed above and I tried to run Armitage after each version and still it gets the same Problem Window Of Death as I now call it.  I Also wasn't sure if I should put the # symbol before writing it like this:

[COLOR=#0000ff]#[/COLOR][COLOR=#0000FF]export MSF_DATABASE_CONFIG=/home/joe/.msf4/database.yml[/COLOR]

So I added the # because it looked like other lines of text in the file had the "#" mark.  I Also don't know if quotes need to be around the part after the = sign?  I just don't know anymore.  
I've tried all I could, i've read every post i could find but also remember I don't understand a lot of them.  It takes me awhile cause I'll be reading a post and then hear something or a term or a concept I won't understand and have to go research that just so I can understand the original article, and then in that secondary article I'll find another concept I dont get and have to research that just so i can understand the secondary article to understand the primary article.  

I'm sorry this post was so long.  I don't expect many people to respond since I'm new and its so long, but I tried to be as thourough as possible and add as many pics as possible.  This took me hours to type up so please dont delete it on me.  If it's in the wrong section I'm sorry, I didn't know where else to put it.  Any help would be greatly appreciated. 

-Joe

---

### Post by dino99 on 2018-05-05
hello newbie ):P

I have no clue about these progs, but a few minutes are enough to find howtos & wikis like that one:
[https://www.geek-kb.com/how-to-install-metasploit-framework-on-ubuntu/](https://www.geek-kb.com/how-to-install-metasploit-framework-on-ubuntu/)

hopes this one will answer your question and solve your issue(s)  :p  I have to say i'm too busy to spend time reading tons of comments.

---

### Post by winter-is-coming on 2018-05-06
I finally figured it out.  For anyone who has trouble installing Armitage using all of the tutorials out there on the internet BEWARE!  I saw in a few places it told me that the file "database.yml" should be copied or moved into a folder called "config" in [B]/opt/metasploit-framework/[COLOR=#b22222]config[/COLOR]/database.yml
[/B]
This is nonsense.  "database.yml" should go directly into "metasploit-framework".  Also in terminal type the command line: [B] MSF_DATABASE_CONFIG=/opt/metasploit-framework/database.yml
[/B]
Also make sure you go into a file called "profile" its in **root/etc/**profile.  Profile is a text document, at the bottom add the line:
[B]# export MSF_DATABASE_CONFIG=/opt/metasploit-framework/database.yml
[/B]

Oh and thank you Dino99 for the response.  It actually did help and led me to the solution eventually.  Thanks so much.

---

### Post by winter-is-coming on 2018-05-09
You may close this thread, it has been resolved

---

