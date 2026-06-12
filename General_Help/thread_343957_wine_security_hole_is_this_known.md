---
title: "wine security hole? is this known?"
date: 2007-01-22
forum: General Help
---

### Post by bash on 2007-01-22
As I was browsing the net today I got a bit curious and was wondering and wanted to see what happens when you run all those "Test your PCs vunerability tests" that there are on the Internet for windows machines.

So I found this one from Greenborder ([http://greenborder.com/test/](http://greenborder.com/test/)) and tried running it in Firefox. But since this is something Internet Explorer specific, I started up my ies4linux and ran the test in there. what it showed I didn't find so comforting. The test creates a folder "called stolen" files, where it copies all the files it was able to get using standart techniques of commen windows worms/trojan/... so on. when I opened that folder after the test I could find a happy collection of different files from my /home/ directory. I guess this comes from the fact that windows defaultly sets your /home/ directory as the windows "my documents". 

Basically this means that you just need to catch some windows malware in wine/ies4linux, which is not the hardest thing in the world and your personal data can happily be exploitet, basically circumventing any protection the linux enviroment normally offers. The questions i guess now remains is how far can windows malware run in a wine enviromnet, but since a lot of normal programs work, i guess quite a few malware ones will as well.

---

### Post by rai4shu2 on 2007-01-22
It's probably not a good idea to view untrusted sites with IE (Wine or Windows). At least with Wine, as long you aren't running it as root, it won't corrupt your system.

If you run winecfg, you can change the folder for "My Documents" under the Desktop Integration tab.

---

### Post by Tomosaur on 2007-01-22
Not sure if it's known or not, it would probably be a good idea to alert the wine folks:
[Click here](http://bugs.winehq.org/). Explain in your bug report about what you did, what your system is etc. If they know about it, they'll just mark it as a duplicate. If not, they'll try to reproduce it (which is why you need to tell them how you came to discover the bug). If they can't reproduce it, it is possible it's an Ubuntu bug, or an ies4linux bug, so you may need to file a bug report in each of those :)

---

### Post by evilghost on 2007-01-22
Wine is not the culprit, instead this security issue is a direct result of symlink traversal.

I always mitigate those vulnerabilities by removing any symlink in ~/.ies4linux/ie6/dosdevices except for c:

The dosdevices symlinks in Wine control what wine has access to via drive letter assignment.  By removing the symlink "z:" which points to "/" you prevent access to the root filesystem since the only remaining symlink will be "c: -> ../drive_c"

To find any symlinks simply run the following command:

```

cd ~/.ies4linux
find -type l

```

It's also necessary to remove the symlinks in ~/.ies4linux/ie6/drive_c/windows/profiles/[username] since they link to your profile.  For example, my username is 'luser'.

```

lrwxrwxrwx  1 luser luser   19 2007-01-22 09:05 Desktop -> /home/luser/Desktop
drwxr-xr-x  3 luser luser 4096 2007-01-22 09:06 Favorites
drwxr-xr-x  5 luser luser 4096 2007-01-22 09:05 Local Settings
lrwxrwxrwx  1 luser luser   11 2007-01-22 09:05 My Documents -> /home/luser
lrwxrwxrwx  1 luser luser   11 2007-01-22 09:05 My Music -> /home/luser
lrwxrwxrwx  1 luser luser   11 2007-01-22 09:05 My Pictures -> /home/luser
lrwxrwxrwx  1 luser luser   11 2007-01-22 09:05 My Video -> /home/luser

```

To mitigate these vulnerabilities run the below code in a terminal which will simply remove these symlinks and create standard directories in their place.

```

cd ~/.ies4linux/ie6/dosdevices
rm -rf z:
cd ~/.ies4linux/ie6/drive_c/windows/profiles/`whoami`
rm -rf Desktop "My Documents" "My Music" "My Pictures" "My Video"
mkdir Desktop "My Documents" "My Music" "My Pictures" "My Video"

```

---

### Post by jelkimantis on 2007-01-22
Windows is a security risk in general, isn't that one reason a lot of use are using Linux?  If I'm not mistaken, you have to go through a lot of gyrations in general to get windows locked down.  If we're running a system which is quasi windows, won't it have many the same security problems as windows, simply because the programs we're trying to run are going to want to have the same behavior coming from the system (that is general write privileges for way too much stuff.)

I agree with the previous posts; it's not getting root access s(unless you're running sudo wine, which I don't know why you would.)

Wine will probably (one day) be able to fix this and restrict it for once and all, but now we're looking at getting wine to run all windows programs without fault.  I think once wine is able to accomplish their main goals, we can start complaining about security holes.  Or you can learn how to code and plug the holes yourself.

Until then, just be careful running wine, if I'm not mistaken is really still in development and listed as unstable in general...

Jelki

---

### Post by evilghost on 2007-01-22
> **jelkimantis said:**
> Wine will probably (one day) be able to fix this and restrict it for once and all, but now we're looking at getting wine to run all windows programs without fault.  I think once wine is able to accomplish their main goals, we can start complaining about security holes.  Or you can learn how to code and plug the holes yourself.

Wine is not the culprit, it's nothing more than symlink traversal.  The ies4linux installation script creates these symlinks.

---

### Post by FrankVdb on 2007-01-22
What do you need IE for under Linux? Development purposes?

---

### Post by ardchoille42 on 2007-01-22
> **ubun-two said:**
> As I was browsing the net today I got a bit curious and was wondering and wanted to see what happens when you run all those "Test your PCs vunerability tests" that there are on the Internet for windows machines.

So I found this one from Greenborder ([http://greenborder.com/test/](http://greenborder.com/test/)) and tried running it in Firefox. But since this is something Internet Explorer specific, I started up my ies4linux and ran the test in there. what it showed I didn't find so comforting. The test creates a folder "called stolen" files, where it copies all the files it was able to get using standart techniques of commen windows worms/trojan/... so on. when I opened that folder after the test I could find a happy collection of different files from my /home/ directory. I guess this comes from the fact that windows defaultly sets your /home/ directory as the windows "my documents". 

Basically this means that you just need to catch some windows malware in wine/ies4linux, which is not the hardest thing in the world and your personal data can happily be exploitet, basically circumventing any protection the linux enviroment normally offers. The questions i guess now remains is how far can windows malware run in a wine enviromnet, but since a lot of normal programs work, i guess quite a few malware ones will as well.

Yes, wine will run Windows viruses, trojans, malware, etc. which is why I don't use it. There are a few good articles from trusted sources stating that wine will run Windows viruses/trojans/malware/etc. The programs you run with wine may not be able to trash the system (due to lack of admin privs), but they can trash or exploit all the files in your $HOME and I consider the files in my $HOME more important than the system files - system files don't contain my private info. Have a look at [this]("http://www.winehq.org/pipermail/wine-devel/2005-January/033294.html") and [this]("http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss").

---

### Post by evilghost on 2007-01-22
> **ardchoille42 said:**
> Yes, wine will run Windows viruses, trojans, malware, etc. which is why I don't use it. There are a few good articles from trusted sources stating that wine will run Windows viruses/trojans/malware/etc. The programs you run with wine may not be able to trash the system (due to lack of admin privs), but they can trash or exploit all the files in your $HOME and I consider the files in my $HOME more important than the system files - system files don't contain my private info.

This is slight misinformation.  Access to the filesystem via wine is controlled via the dosdevices symlinks as well as any other symlinks found with-in ~/.wine as wine will traverse them.

A properly configured wine setup will mitigate these vulerabilities **however** execution of viruses with-in wine is still possible; damage to the filesystem outside of ~/.wine isn't.

---

### Post by bodhi.zazen on 2007-01-22
> **ardchoille42 said:**
> Yes, wine will run Windows viruses, trojans, malware, etc. which is why I don't use it. There are a few good articles from trusted sources stating that wine will run Windows viruses/trojans/malware/etc. The programs you run with wine may not be able to trash the system (due to lack of admin privs), but they can trash or exploit all the files in your $HOME and I consider the files in my $HOME more important than the system files - system files don't contain my private info. Have a look at [this]("http://www.winehq.org/pipermail/wine-devel/2005-January/033294.html") and [this]("http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss").

While I border on paranoid, how do you draw these conclusions from your citations ???

First one:
> My original email was to correct a slight factual inaccuracy in the
text, not to get anybody worried. [b][color=red]The chances of this actually being a
problem are so close to zero that it's not worth thinking about.[/color][/b]


Second one:
> **[color=red]Out of the five Windows viruses I ran under Wine, not a single one was able to send email and propagate itself.[/color]**

Where is a citation to support > **[color=blue]There are a few good articles from trusted sources stating that wine will run Windows viruses/trojans/malware/etc. The programs you run with wine may not be able to trash the system (due to lack of admin privs), but they can trash or exploit all the files in your $HOME and I consider the files in my $HOME more important than the system files - system files don't contain my private info.**[/color]

I am not aware of any citation to support your FUD.

---

### Post by ardchoille42 on 2007-01-22
> **evilghost said:**
> This is slight misinformation.  Access to the filesystem via wine is controlled via the dosdevices symlinks as well as any other symlinks found with-in ~/.wine as wine will traverse them.

A properly configured wine setup will mitigate these vulerabilities **however** execution of viruses with-in wine is still possible; damage to the filesystem outside of ~/.wine isn't.

So, any app that you use through wine, that keeps private info on disk (such as a banking site in IE in wine).. that info can be exploited if you run a virus/trojan/malware in wine? What happens when a person unknowingly runs an app in wine that installs a keylogger or mouse mapper? Won't that catch things? Like the sudo password? We all know how insecure IE is and many people run IE in wine because some, if not most, banking sites require IE.

---

### Post by bash on 2007-01-22
well a keylogger under wine couldn't directly log your root pass unless you would enter it inside a wine application. and of course it can't access sys files, since (normally) ur running wine as user not root. but malware is still able to exploit your /home/ directory and at least for me all of my important stuff is saved there.

but yea guessed the direct fix would be to remove wine access to the so called ":z" drive. but didn't know how to. evilghost explained that very good.

and i use ies4linux for my uni. some pages only run with internet explorer.

and besides that is there a way to forbid wine access to the internet?

---

### Post by ardchoille42 on 2007-01-22
> **ubun-two said:**
> ..is there a way to forbid wine access to the internet?

Not a bad idea. But, wouldn't that prohibit ie4linux from operating correctly? Check [this]("http://ubuntuforums.org/showthread.php?t=72598") out :)

It's just my opinion, but I feel that wine brought all the bad things from Windows to Linux.

---

### Post by bash on 2007-01-22
yes it would prohibit ies4linux accessing the internet. but im mainly concerned for my install of crossover, which is also based on wine. im running it coz my uni requires powerpoint presentations and i ran into quite some trouble with openoffice, since presentations i made on it turned out completly messed up in powerpoint. 

but to make sure that at least to that wine uninstall no harm can be done i wanted to restrict the internet access of it.

---

### Post by bodhi.zazen on 2007-01-22
> **ardchoille42 said:**
> It's just my opinion, but I feel that wine brought all the bad things from Windows to Linux.

:---) FUD 

Citation please ? Do you have a single citation to back your claims ? If you do I would be extremely interested.

---

### Post by evilghost on 2007-01-22
> **ardchoille42 said:**
> So, any app that you use through wine, that keeps private info on disk (such as a banking site in IE in wine).. that info can be exploited if you run a virus/trojan/malware in wine? What happens when a person unknowingly runs an app in wine that installs a keylogger or mouse mapper? Won't that catch things? Like the sudo password? We all know how insecure IE is and many people run IE in wine because some, if not most, banking sites require IE.

A keylogger installed through wine will only work for applications run in wine, and even then it may be unlikely that it would work successfully.  It will not catch the sudo password as the sudo application runs outside of wine.

---

### Post by ardchoille42 on 2007-01-22
> **bodhi.zazen said:**
> :---) FUD 

Citation please ? Do you have a single citation to back your claims ? If you do I would be extremely interested.

Not that I have to explain my "opinions" to you, but 

[http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)

[http://www.winehq.org/pipermail/wine-devel/2005-January/033294.html](http://www.winehq.org/pipermail/wine-devel/2005-January/033294.html)

[http://blogs.zdnet.com/Ou/index.php?p=146](http://blogs.zdnet.com/Ou/index.php?p=146)

Well, you get the idea. The point is, if wine can run Windows exploits/viruses/trojans/malware, then wine is not a good thing to use. The Register even ran an article that showed how easy it is to run Windows viruses and trojans in wine.

Not only those, but there are viruses listed as compatible in the wine compatibility list. There are a lot of "citations" all over the internet that show viruses/trojans/malware running just fine in wine.

Would you like to appologize for the FUD comment now?

---

### Post by rai4shu2 on 2007-01-22
You might want to read those articles you posted links to. Their conclusions may surprise you.

---

### Post by ardchoille42 on 2007-01-22
*sigh*

Yes, people often see what they want to see when reading articles.

---

### Post by bodhi.zazen on 2007-01-22
> **ardchoille42 said:**
> Not that I have to explain my "opinions" to you, but 

[http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)

[http://www.winehq.org/pipermail/wine-devel/2005-January/033294.html](http://www.winehq.org/pipermail/wine-devel/2005-January/033294.html)

Not only those, but there are viruses listed as compatible in the wine compatibility list. There are a lot of "citations" all over the internet that show viruses/trojans/malware running just fine in wine.

:^o [size=4][color=red]Rubbish[/size][/color] :^o

Healthy paranoia is mandatory for security, but you are spreading unsubstantiated FUD.

I responded to your "references" in my first post and [color=red]neither reference supports your claim[/color].

> There are a lot of "citations" all over the internet that show viruses/trojans/malware running just fine in wine.

Not true, I could not find a single citation on the internet ever remotely supporting this wild claim.

I did a google search "run window viruses on wine"  [http://www.google.com/search?q=run+window+viruses+on+wine&ie=utf-8&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=run+window+viruses+on+wine&ie=utf-8&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a)

google search "malware on wine" [http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla:en-US:official&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=malware+on+wine&spell=1](http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla:en-US:official&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=malware+on+wine&spell=1)

:^o [color=red]**[size=2]There are no citations to support your FUD[/color]**[/size]  :^o

---

### Post by bodhi.zazen on 2007-01-22
> **ardchoille42 said:**
> *sigh*

Yes, people often see what they want to see when reading articles.

so you read (this is in your own citation I might add)

> ... not a single one was able to send email and propagate itself.

As > **ardchoille42 said:**
> There are a lot of "citations" all over the internet that show viruses/trojans/malware running just fine in wine.

Pure FUD ...

There are a number of citations citing potential issues and discussion of patches to wine but nothing to support your level of paranoia.

EDIT: just saw your edit:

> **ardchoille42 said:**
> Would you like to appologize for the FUD comment now?

As soon as you tone down your FUD ;)

---

### Post by FrankVdb on 2007-01-23
> **ardchoille42 said:**
> We all know how insecure IE is and many people run IE in wine because some, if not most, banking sites require IE.

That's fairly prehistoric, you ought to make clear to your bank that this is 2007.

My bank (I'm in Belgium) uses a browser-independent system which is 100% safe against  tampering because you need your card, a small decoding device, the card number and your PIN code to access your account through the internet. If you need to install anything onto your PC, you're creating a vulnerability that can be exploited over the net.

Browser-dependent banking systems are fully outdated, unsafe and, on top of that, insulting for Linux users.

---

### Post by evilghost on 2007-01-23
> **FrankVdb said:**
> That's fairly prehistoric, you ought to make clear to your bank that this is 2007.

My bank (I'm in Belgium) uses a browser-independent system which is 100% safe against  tampering because you need your card, a small decoding device, the card number and your PIN code to access your account through the internet. If you need to install anything onto your PC, you're creating a vulnerability that can be exploited over the net.

Browser-dependent banking systems are fully outdated, unsafe and, on top of that, insulting for Linux users.

I refuse to do business with sites which require IE to proceed/function.  I imagine there are many people who take this same position.

---

### Post by ozp on 2007-01-23
I think that the more important issue here is about wine security hole.

The windows, browser, linux, bank issue is not important

Since we need wine and Ie4linux for whatever reason, we want to know if this is secure or not

If its not secure what we have to do to still use wine and ie4linux and be secure

---

### Post by ozp on 2007-01-23
> **evilghost said:**
> Wine is not the culprit, instead this security issue is a direct result of symlink traversal.

I always mitigate those vulnerabilities by removing any symlink in ~/.ies4linux/ie6/dosdevices except for c:

The dosdevices symlinks in Wine control what wine has access to via drive letter assignment.  By removing the symlink "z:" which points to "/" you prevent access to the root filesystem since the only remaining symlink will be "c: -> ../drive_c"

To find any symlinks simply run the following command:

```

cd ~/.ies4linux
find -type l

```

It's also necessary to remove the symlinks in ~/.ies4linux/ie6/drive_c/windows/profiles/[username] since they link to your profile.  For example, my username is 'luser'.

```

lrwxrwxrwx  1 luser luser   19 2007-01-22 09:05 Desktop -> /home/luser/Desktop
drwxr-xr-x  3 luser luser 4096 2007-01-22 09:06 Favorites
drwxr-xr-x  5 luser luser 4096 2007-01-22 09:05 Local Settings
lrwxrwxrwx  1 luser luser   11 2007-01-22 09:05 My Documents -> /home/luser
lrwxrwxrwx  1 luser luser   11 2007-01-22 09:05 My Music -> /home/luser
lrwxrwxrwx  1 luser luser   11 2007-01-22 09:05 My Pictures -> /home/luser
lrwxrwxrwx  1 luser luser   11 2007-01-22 09:05 My Video -> /home/luser

```

To mitigate these vulnerabilities run the below code in a terminal which will simply remove these symlinks and create standard directories in their place.

```

cd ~/.ies4linux/ie6/dosdevices
rm -rf z:
cd ~/.ies4linux/ie6/drive_c/windows/profiles/`whoami`
rm -rf Desktop "My Documents" "My Music" "My Pictures" "My Video"
mkdir Desktop "My Documents" "My Music" "My Pictures" "My Video"

```


I did this.
Is my box secure now?

---

### Post by evilghost on 2007-01-23
> **ozp said:**
> I did this.
Is my box secure now?

In the scope of this thread, yes.  However, note that Internet Explorer is inherently insecure.

---

### Post by bodhi.zazen on 2007-01-23
> **ozp said:**
> I think that the more important issue here is about wine security hole.

The windows, browser, linux, bank issue is not important

Since we need wine and Ie4linux for whatever reason, we want to know if this is secure or not

If its not secure what we have to do to still use wine and ie4linux and be secure

You see that is the problem with FUD :(

There is a potential security issue, but ardchoille42 did not cite a single instance where this has actually happened. ardchoille42 citation lists a "potential" problem with wine (I say potential because there is no report of an actual security breach, just a potential) in combination with Micorsoft products (IE) and, to quote the source,:

> All applications launched inside Wine, Cedega, or Cross-Over Office are technically still exploitable. Wine runs on most x86 platforms, including Linux and the various BSDs.  The surprising part about finding this flaw in Wine is that they implemented the entire Meta File API without realizing that this could be a security issue. **Exploiting a Windows application** running inside Wine depends on that application calling the vulnerable function with malicious data. The most feasible way this could happen is via a malicious WMF file embedded into a Word document, opened in Microsoft Office and running under Cross-Over Office.

**Marcus Meissner (meissner@suse.de) contacted the Wine development team and sent them a patch to fix this flaw.**

**Note:**[list=number][*]The "potential problem" is with microsoft applications (IE) in combination with wine.
[*]A patch has already been sent to wine.
[*]Again, no citation of an actual breach, just a potential.[/list]

The security flaw is with IE (no surprise there :) ) as you can run wine with non-microsoft products without a security issue.

The best you can do is to use linux native programs as much as possible and keep wine up to date.

My advice is:

If you use IE for sensitive information, such as internet banking, in Linux or windows, **STOP IT**

As evilghost says, I would change banks to one which does not require IE for internet banking. This is much more secure and it is not difficult to find a more reasonable, secure financial institution.

---

### Post by bodhi.zazen on 2007-01-23
> **ozp said:**
> I did this.
Is my box secure now?

The only secure box is one that is turned off, disconnected from the internet, and in a locked room :p

You box is reasonably secure.

IMO, Your use of IE is and always will be a potential security flaw due to the inherent flaws of IE.

---

### Post by ozp on 2007-01-23
we all know that IE is insecure and ie4linux is insecure too.

just a few people will be crazy enough to do banking with ie4linux

I have this to see sites that does not open in FF, and also for some testing

---

### Post by bodhi.zazen on 2007-01-23
> **ozp said:**
> we all know that IE is insecure and ie4linux is insecure too.

just a few people will be crazy enough to do banking with ie4linux

I have this to see sites that does not open in FF, and also for some testing

Yea, sure we all understand these realities as well, although I will still protest use of sensitive information such as online banking ;)

My objection has been to what I feel have been exaggerations of the risks or running wine. Such FUD clouds the issue because less users with less experience or knowledge no longer know how to maintain a secure system.

---

### Post by ozp on 2007-01-24
thats is my case.

I'm using ubuntu and for the first time I have a linux box to be my main box.
I have being trying and using linux since 1998 but never was able to install and use as a main system

The only think that still need to be done is to make the fonts looks nice in openoffice (like they look on windows) (I have installed mscorefonts and I have the windows fonts too)

I was even wondering if something comes in thunderbird if its possible to be damaged

---

### Post by YokoZar on 2007-01-25
> **bodhi.zazen said:**
> [*]A patch has already been sent to wine.This issue was plugged over a year ago, before the Wine that's included in Dapper even came out.  Don't worry about wmf files anymore.

As for security with Wine...

Yes, if Wine has access to your home directory (eg, you use the default mapping created by Winecfg), then running a malicious Windows app can potentially trash your home directory.  But the same is true of any malicious script or program run by your user account.

Most malicious Windows software, however, is not designed for Wine environments and will instead just try and trash the Windows drive.  Fortunately, if such a thing occurs it's pretty damn easy to start fresh with Wine - just move your important data, rm -rf ~/.wine, and then run winecfg again.  In Windows, flattening and reinstalling can take several hours.

---

### Post by Ramses de Norre on 2007-01-25
If you're really paranoia you could set up a chroot jail to run wine in, that way you're sure wine wont touch anything outside the jail. But it requires some time to set it up though..

---

### Post by Enverex on 2007-01-25
ies4linux uses a modified version of Wine and thus this isn't a Wine issue, it's an "ies4linux" issue, so if you find any issues you need to take them up with the ies4linux team rather than Wine itself.

If you want security in Wine simply set up only a virtual C: drive in a folder and your CD driver via winecfg and that way malicious Windows apps cannot touch anything outside of your fake C: drive folder.

---

### Post by bodhi.zazen on 2007-01-25
> **YokoZar said:**
> This issue was plugged over a year ago, before the Wine that's included in Dapper even came out.  Don't worry about wmf files anymore.

[QUOTE=Ramses de Norre;2061292]If you're really paranoia you could set up a chroot jail to run wine in, that way you're sure wine wont touch anything outside the jail. But it requires some time to set it up though..

> **Enverex said:**
> ies4linux uses a modified version of Wine and thus this isn't a Wine issue, it's an "ies4linux" issue, so if you find any issues you need to take them up with the ies4linux team rather than Wine itself.

If you want security in Wine simply set up only a virtual C: drive in a folder and your CD driver via winecfg and that way malicious Windows apps cannot touch anything outside of your fake C: drive folder.

Thank all 3 of you for speaking up. :p

---

