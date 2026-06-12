---
title: "FireFox hijacked AGAIN"
date: 2014-02-21
forum: General Help
---

### Post by Barney-R on 2014-02-21
What's **wrong** with FireFox? Why can't Mozilla DO something about all these vulnerabilities?

Today I've acquired yet **another** hijacker, and this one even stops me logging in to the Ubuntu forums, forcing me to use the Opera browser.

I don't even have to click on a link. If I click **anywhere** in FireFox (to select some text for example) I get a pop-up with the URL

http://fixbonus.com/lp7/

I haven't installed any add-ons for several months (not many installed anyway), and I haven't been to any unfamiliar sites, so where does this stuff keep coming from?

If I click on a link, the wanted page opens, but so does the annoying "fixbonus" pop-up, in a separate **window** (not a tab) with it's auto-running sound file, and it's in front of everything else.

I was able to get to the Ubuntu forum log-in page using FireFox, but that was as far as I got. It wouldn't let me log in.

I'm aware that I can get rid of hijackers by renaming, and then deleting, a folder in FireFox (I've had to do it twice so far to get rid of the adf.ly hijacker), but that gives me a "clean" installation with none of my preferences, add-ons or bookmarks, so I'd rather try something else this time.

Doesn't FireFox have some way of blocking specific URLs? If not, it should.

Sorry. I know it's a FireFox problem rather than an Ubuntu problem, but these repeated hijackings are driving me round the twist. I've tried Googling the hijacker in the hope of getting rid of it, but without success. No (relevant) results. It's as if no-one's heard of this particular hijacker.

One final point. I'm not very familiar with the terminal, so if I have to do it that way, please keep it simple.

---

### Post by SuperFreak on 2014-02-21
Try installing security addons for Firefox such as Ghostery, Noscript etc

---

### Post by Habitual on 2014-02-21
time for a new firefox profile maybe?

---

### Post by Barney-R on 2014-02-21
I think I've found the problem. A long time ago I installed an add-on called DownloadHelper for the occasional download of certain copyright-free (permission given by owner) YouTube videos.

I hadn't used it for ages, and when I tried it a couple of times late last year, I found it didn't work any more, so I just left it there rather than remove it.

That seems to have been the source of this latest hijacking, but I don't know what triggered it. I hadn't tried to use it because I knew it didn't work.

I started FireFox in safe mode, and the "fixbonus" hijacker didn't appear, so I worked through all the "doubtful" add-ons until I found the one that was causing the trouble.

For protection I've got

Adblock Plus 2.4.1
BetterPrivacy 1.68
BrowserProtect 1.13 (except that it didn't)
Ghostery 5.1.1
NoRedirect 1.3.2.13

Plus six others unconnected with security that I find useful, and the Ubuntu Firefox Modifications. Nothing else.

I'm not sure about NoScript. Would it interfere with anything legitimate, or **should** I install it?

Now I just keep everything crossed and hope this particular hijacker won't bother me any more.

I'll give it a week, just to be sure, and then mark the thread as solved. Thanks to both of you for your suggestions.

---

### Post by Barney-R on 2014-02-21
No good. The hijacker's still there. I'll install NoScript and see what happens.

---

### Post by Barney-R on 2014-02-21
Good news! (I hope). I've installed NoScript 2.6.8.14 and so far, no hijacking. I've also removed a couple of add-ons that failed to protect me from this malware (Browser Protect and No Redirect).

---

### Post by SuperFreak on 2014-02-21
I believe NoScript prevents JAVA and JavaScript applications from working unless authorized by user. I don't use it personally as I have uninstalled JAVA which is a quite common source of exploits

---

### Post by buzzingrobot on 2014-02-21
Toggle between java enabled/disabled and javascript enabled/disabled.  You may narrow it down to java and then you can disable it permanently.  That's not much of a loss. I never enable it and nothing has ever complained.

you can effectively ban ip's via /etc/hosts.

---

### Post by coldcritter64 on 2014-02-21
> **Barney-R said:**
> Good news! (I hope). I've installed NoScript 2.6.8.14 and so far, no hijacking. I've also removed a couple of add-ons that failed to protect me from this malware (Browser Protect and No Redirect).

In my experience of using firefox, especially when using it in Windows, I've always used it with noscript and never been seriously hijacked. 

Using Firefox with noscript on Linux, I've even hit a site that I allowed the scripting for deliberately, suspecting the site was dodgy (not recommended btw, ;)). it seized the browser solid on me; It would have massacred my old Windows setup no doubt. Turned out the site was blocked a day or so later by mozilla (I went back for a second go and got a red Mozilla warning page about a hijack site etc :lol:).

All I did was force kill the browser with a terminal (yes, necessary...it just wouldn't respond otherwise), cleared out my firefox profile (good to have a clean backup of your profile stored away) and restarted in minutes. Noscript is a must have addon for me. Cheers.

> I believe NoScript prevents JAVA and JavaScript applications from working unless authorized by user....Yes, and permissions can be set temporarily for sites you are visiting (maybe for the first time) until you get to know if you "trust" them or not. 

If you regularly visit a site, you can set permanently held (whitelisted) permission for sites to work more seamlessly.

---

### Post by Barney-R on 2014-02-25
Sorry. Got called away for a few days.   Some good suggestions there. I'm finding NoScript to be a bit of a pain. It's not responding according to the preferences I've set, it's not giving me the option to "allow" or "temporarily allow" anything, though the boxes are ticked in "preferences", and even when I allow a site, I still get that annoying message at the bottom of the screen that won't go away until I close it manually. Perhaps I need to remove NoScript and try again? If not, I'm strongly tempted to remove it altogether.  Disabling Java seems like a good idea, if only as a test, but how do I do it and how do I re-enable it? It doesn't appear to be an option in FireFox preferences.   I haven't seen the hijacker yet this week, but even after installing NoScript last week, it was still appearing occasionally.   I hadn't realised Ubuntu had a hosts file, though I used it in the bad old days when I used Windoze. How does it work in Ubuntu though? I find I have hosts and hosts.deny. Which one should I use? Common sense would suggest hosts.deny, but is that the right one?   Once I've got the right hosts file open, how do I tell it to block a particular site?  The complete URL I'm concerned with at present is  http://fixbonus.com/lp7/  I've seen differerent values for lp (not always 7), so presumably I need to block  http://fixbonus.com/*   I'm not entirely sure what I'm doing here though, so I'd appreciate it if someone could tell me exactly what I need to enter, and in which hosts file.  Perhaps then I'll be able to rid myself of the annoying NoScript.

---

### Post by Barney-R on 2014-02-25
Now this site isn't behaving as it should. I've lost the option to use bold (or other attributes) and even though I separate my post into paragraphs, when I post it, it appears as a solid block of text. I hope that won't make it too difficult to understand. Presumably it's the hijacker still causing problems.

---

### Post by buzzingrobot on 2014-02-25
Assuming some malicious code is running, you need to locate and remove it. Adding gizmos that say they will prevent future infections doesn't seem to be doing that. You could try removing Firefox (use the purge option to delete the config files, then doublecheck to be sure all its config files are gone,  searching for other files referencing it and removing them.  Then, reinstall Firefox and see what happens.

The Java plugin can be disabled via Tools->Add-Ons->Plugins. It's called the "Iced-Tea Web Plugin".

---

### Post by maglin2 on 2014-02-25
A windows example of this malware seems to have resulted from a surreptitiously added plugin (rather than an add-on extension) - you don't have any additional plug-ins do you? Alternatively you could set all your plugins to 'Ask to activate' and see if the problems stop.

---

### Post by SeijiSensei on 2014-02-25
I'd just create a new Firefox profile and start from scratch.  First, use Ctrl-Shift-O to bring up the bookmark manager and backup your current bookmarks to a json file.  Now open a terminal and type
```

cd ~/.mozilla
mv firefox firefox.bad

```
Reopen Firefox.  You will now have the default browser configuration.  Use the bookmark manager to import your saved bookmarks.

From here you can start to reinstall add-ons and extensions.  I never liked NoScript; like you I found it too intrusive.  I rely on AdBlock Plus and Ghostery which have worked pretty well for me over the years.

---

### Post by monkeybrain20122 on 2014-02-25
This has never happened to me, but a guy I installed lubuntu for did get hijacked. Basically I just removed the .mozilla folder and it was fixed I think he got it from some sport sites. I can't remember where the hijacker took the browser to now but at that time I noted that and examined the modified entries in about:config. Googling found that it was a Windows malware, it was odd that this guy got it on Linux too, though from the descriptions I found on google if he was running Windows the consequence would be much worse because it would spread beyond the browser and modify the registry in Windows.

---

### Post by monkeybrain20122 on 2014-02-25
> **buzzingrobot said:**
> Toggle between java enabled/disabled and javascript enabled/disabled.  You may narrow it down to java and then you can disable it permanently.  That's not much of a loss. I never enable it and nothing has ever complained.

you can effectively ban ip's via /etc/hosts.

You can set java to "activate when asked" in Firefox's Tools > Addons > Plugins, same for flash (there is really no need for  flashblock as the ability to activate flash on demand is built in now)

---

### Post by Barney-R on 2014-02-25
Thank you all for you advice. I've finally come to the conclusion that it's not worth trying to fix the problem on the present setup, so I **will** reinstall firefox.

buzzingrobot, I appreciate your advice on how to disable Java. That's something I've learned today.

SeijiSensei, before I use it, could you (or someone else) explain what that terminal command actually does? I'm still a beginner where the terminal is concerned, and there never seems to be enough time to read up on the various commands.

---

### Post by monkeybrain20122 on 2014-02-25
> **Barney-R said:**
> Thank you all for you advice. I've finally come to the conclusion that it's not worth trying to fix the problem on the present setup, so I **will** reinstall firefox.
.

Reinstall Firefox is useless because your profile and settings will stay. Instead all you need is to remove the hidden folder .mozilla. 

Maybe that's why your problem persists (you said "again" in the title) In Linux the executable and system files are separated from user settings, the latter are in your home. The malware cannot touch the system part so by reinstalling you are trying to fix the problem by removing the part that has not been affected while keeping the compromised part intact.

---

### Post by 1clue on 2014-02-25
I don't know what sort of web sites you visit, but I use Firefox on Windows, Mac and Linux all the time.  I've never been hijacked.

One thing I don't do is download software from anywhere except the official site.  Any "Download Helper" or similar "helper" or toolbar widget is essentially spyware or malware.  Don't install that stuff.  If you have to, then read the license agreement all the way through.  If they try to convince you to install something else in addition to what you went there for you should be extremely suspicious.  It's gonna be spyware or some other malware.

Just about all I use as a plugin is Firebug since I develop Internet apps.

---

### Post by dragonfly41 on 2014-02-25
Here is another perspective at the risk of drowning you with more information.

If you go back to the rogue site you're trying to purge .. http:/ /fixbonus.com/lp7/
right click on the page .. and you see the source code.

There is a block of code showing that this is an Adobe flash file

```

<div class="textwidget">
<object data="files/player.swf" name="obj-pro-player-2pp-single-525b2cf3b80e0" id="obj-pro-player-2pp-single-525b2cf3b80e0" type="application/x-shockwave-flash" height="100%" width="100%"><param value="transparent" name="wmode"><param value="true" name="allowfullscreen"><param value="always" name="allowscriptaccess"><param value="all" name="allownetworking"><param value="width=410&amp;height=275&amp;autostart=true&amp;repeat=false&amp;backcolor=111111&amp;frontcolor=cccccc&amp;lightcolor=66cc00&amp;stretching=fill&amp;enablejs=true&amp;mute=false&amp;skin=files/default.swf&amp;plugins=&amp;streamer=rtmp://r.null.eyan.netdna-cdn.com/play&amp;javascriptid=2pp-single-525b2cf3b80e0&amp;image=&amp;file=files/amp.xml&amp;sid=1381706995" name="flashvars"></object></div>

```

This code shows a streaming video.

If you go into Firefox > Tools > Plugins you will see typically Shockwave Flash 11.2.202.451

You can temporarily change this setting from "Always Activate" to "Ask to Activate".

However this will only block the embedded video but will not block the site coming up again.

One effective way of blocking this site (and others) is to go to [www.opendns.com]("http://www.opendns.com") and setup a Web Filter > Home (free) account and setup the filters (black list).

Here are notes which I jotted down when setting this up.

[COLOR=blue]
opendns.com

Configuration for Ubuntu

Right-click on &#8216;Network Icon&#8217; (located at top-right panel by default) and click on &#8216;Edit Connections&#8217; to open Network Connections Manager.

Choose the type of connection you have. For this example, we will use &#8216;Wired&#8217;.

Under &#8216;Wired&#8217;, highlight &#8216;Auto etho&#8217; and click on &#8216;Edit&#8217;.

Inside 'Editing Auto etho' window, click on &#8216;IPv4 Settings&#8217; tab.

Under &#8216;IPv4 Settings&#8217;, change the &#8216;Method&#8217; to Automatic (DHCP) addresses only.

Put these nameserver addresses as your &#8216;DNS Servers&#8217;: 208.67.222.222, 208.67.220.220

Click &#8216;OK&#8217; and reboot your machine. You can then visit [http://welcome.opendns.com](http://welcome.opendns.com) to confirm you are using OpenDNS.
 
[/COLOR]

---

### Post by buzzingrobot on 2014-02-25
> **Barney-R said:**
> 
buzzingrobot, I appreciate your advice on how to disable Java. That's something I've learned today.



Good luck with the new installation.[/quote]

BTW, "mv" is the command to move something someplace. It has the effect of copying something to a new location, then deleting it in its original location. "~" is shorthand for a user's home directory. "cd" is "change directory".  So, "cd ~" will put you back in your home directory.

"~/.mozilla" is a directory created in your home directory when you install Firefox. Inside it is the "Firefox" directory, which contains the configuration files specific to your installation. E.g., when you change something in Firefox preferences, you are changing a file in that directory.

If you are in the ~/.mozilla directory, the command "mv firefox foirefox.bad" will move the firefox directory and everything inside it to a new directory called "firefox.bad".  The point here is that the next time you launch Firefox, it will find none of it's configuration data, assume this is the first time it has been executed on the machine, and start afresh.

(Terminal commands are often very terse because they date back to the days when Unix was only a character-based OS, when hardware was not capable of supporting a GUI. If someone spent their time banging on a keyboard to keep a network of Unix machines working, the less keystokes, the better.)

---

### Post by 1clue on 2014-02-25
If you persistently go to sites where there is a problem, perhaps you should create a new user account, log in as that user and use your browser.  This new user account should be completely normal, not privileged in any way.

If you ran your browser in a privileged mode (sudo firefox) then you are asking to have your system compromised.  If you accidentally allowed a key logger to be installed, then you've fallen victim and should learn to do better next time.

If you have a non-privileged account to run this stuff from, then the only thing they can trash is that user's directory.  Set up the user using defaults, and find ways where your normal user can access files downloaded.  You need to leave folder permissions as-is, don't loosen anything up at all for your normal user or any limited user.

If you do this, it would be extremely unlikely that the entire system be compromised.  Then all you might need to do is remove the user, create another user and start over that way.

---

### Post by monkeybrain20122 on 2014-02-25
> **1clue said:**
> If you persistently go to sites where there is a problem, perhaps you should create a new user account, log in as that user and use your browser.  This new user account should be completely normal, not privileged in any way.
.

Or just log into the guest session.

---

### Post by Barney-R on 2014-03-06
Sorry I've been away so long. Sometimes life just gets in the way.

Some excellent information here, and I particularly like the suggestion to use a guest session any time I intend to visit a "suspect" site. I've got a method of transferring files between identities, so that won't be a problem.

I normally only visit a few trusted sites and do my best to avoid anything "dodgy", but sometimes we can't be sure when we click on a link. In this case though, the problem seems to have been caused by a FireFox add-on. I had a similar problem once before (different hijack destination), and someone on here found the offending line in one of my add-ons, so I deleted the .mozilla folder and the problem was solved.

I've uninstalled FireFox, checked that the .mozilla folder was gone, rebooted and reinstalled from the Software Center, and I've disabled Java. I've also installed only the bare minimum of add-ons (not that I had many), Better Privacy, Ghostery and a few others I find useful. I haven't reinstalled Ad-Block Plus yet because I want to find out how certain sites perform without it, but I'll probably install it in the next few days. NoScript was just too much of a pain, being too intrusive, and it wouldn't do what I told it to do (in preferences), so I'll manage without it unless a need arises.

Thanks to everyone for all your help. I'll mark this thread as solved.

---

### Post by Barney-R on 2014-03-06
I'm not sure this is the right way to do it, but I **think** I've managed to work out how to mark the thread as solved.

---

### Post by sandyd on 2014-03-06
> **Barney-R said:**
> I'm not sure this is the right way to do it, but I **think** I've managed to work out how to mark the thread as solved.

Thread tools -> mark thread as solved

---

### Post by eliezer2 on 2014-03-06
I had experienced something like this before but that was because I installed some rubbish software. I had to reinstall firefox to solve the problem. I don't think it is a problem with firefox.
Also if you plan to reinstall, There is an option to backup your bookmarks so that you can import it after reinstallation.

---

### Post by Barney-R on 2014-03-07
Thank you, sandyd. I've done it now.

eliezer2 - That's what I did, so it didn't take long to get everything back the way I wanted it.

Thanks again to everybody for all your good advice.

---

