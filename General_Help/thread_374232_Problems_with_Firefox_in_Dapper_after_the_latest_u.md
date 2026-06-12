---
title: "Problems with Firefox in Dapper after the latest update"
date: 2007-03-02
forum: General Help
---

### Post by WW on 2007-03-02
I updated Firefox (along with some other packages) a few minutes ago.  This update fixed the problem that was causing Evolution to crash (but since I hadn't done the earlier Firefox update, I hadn't run into that problem).  Now Firefox is broken--I have found two problems:

Edit->Preferences does nothing.  I click on it, but a Preferences window does not come up.

Tools->Extensions results in a yellow error window, which says
> 
XML Parsing Error: not well-formed
Location: chrome://mozapps/content/extensions/extensions.xul?type=extensions
Line Number 1, Column 10:

sDblClick(event)"
---------^

I have the "AdBlock Plus" extension installed.

Anyone else having a problem with the latest Firefox update in Dapper?  Any idea how to fix this?

---

### Post by cookfromfrozen on 2007-03-02
Try starting with a new profile.

Go into your home folder, click View > Show Hidden Files.

Rename the **.mozilla** directory to something else, e.g. **.mozilla1**.

If Firefox works later, it is a problem with your configuration.

If not, try the following command:

```

sudo dpkg-reconfigure firefox
sudo apt-get reinstall firefox
```

(You may have to use "mozilla-firefox" instead of "firefox" on Dapper.)

Hope this helps.

---

### Post by WW on 2007-03-02
Thanks for the suggestions!  However...

Renaming .mozilla did not help.

Running dpkg-reconfigure and reinstalling firefox also did not help.  I still get nothing when I try to use Edit->Preferences, and I still get the error when I try Tools->Extensions.

By the way, I think you meant
>  sudo apt-get install --reinstall firefox
There is no 'reinstall' apt-get command.

---

### Post by djripple on 2007-03-02
XML Parsing Error: not well-formed
Location: chrome://browser/content/bookmarks/addBookmark2.xul
Line Number 1, Column 4:kin/bookmarks/addBookmark.css"?>
---^

error I get when new firefox in Dapper.  Tried your solutions and didn't work.. how do I go all the way back to the original firefox that came with dapper??

thanks in adv.

---

### Post by cogitordi on 2007-03-02
Something is not so good. Firefox 1.1.5.10 on Drake is broken for me, too. As is Epipany, which suggests that it's a common library. I try to access Gmail with Firefox and I see the error:

```
Unexpected response from server

Firefox doesn't know how to communicate with the server.

    *   Check to make sure your system has the Personal Security Manager
          installed.

    *   This might be due to a non-standard configuration on the server.
```

I try with Epiphany and I see:
```
&#8220;www.google.com&#8221; requires an encrypted connection.

The document could not be loaded because encryption support is not installed.
```

But Opera opens Gmail correctly, as does Firefox 1.1.5.10 running in Windows NT4.0/Vmware on the **same computer**.

---

### Post by djripple on 2007-03-02
I had the same problem.  Here is the quick solution to [COLOR="Red"]RETURN TO THE ORIGINAL FIREFOX[/COLOR]. or [COLOR="Red"]DOWNGRADE FIREFOX[/COLOR]

[COLOR="Red"]sudo aptitude install firefox/dapper
[/COLOR]

---

### Post by JohnPhys on 2007-03-02
I'm getting the same errors as cogitordi, but only on certain sites.  Anyone else notice this?

---

### Post by WW on 2007-03-02
Well, I just rebooted, and now Firefox is working again.  I can use Edit->Preferences, and Tools->Extensions is working again.   I'm pretty sure I exited Firefox and started it again after the update, so I don't know why a reboot was necessary.  Go figure.

---

### Post by JohnPhys on 2007-03-02
I tried a reboot and it didn't work, though a 

```
sudo apt-get install --reinstall firefox
```

fixed the issue for me (I was getting the security issues, was able to access preferences just fine).

EDIT:  Firefox is broken again!  I didn't change anything, just opened up another browser, and I can't access encrypted sites!

---

### Post by cogitordi on 2007-03-02
dpkg and apt-get did not fix this for me. Still no access to secure sites (including banking) using Firefox and Epiphany in the Drake. 

Again, Firefox works as always in Windows through Vmware.

---

### Post by JohnPhys on 2007-03-02
hmm, the other thing I did was install the mozilla-psm package (before I did apt-get install --reinstall firefox), but I'm not sure that this did anything.

EDIT:  I have the problem again!  I can't access encrypted sites through firefox!

---

### Post by cogitordi on 2007-03-03
No, that fixes nothing for my Firefox. Given that the mozilla-psm package installs Mozilla, I can however use Mozilla to do banking and access Gmail. ;^)

---

### Post by JohnPhys on 2007-03-03
AHH!

Now my encrypted sites don't work?!

I *swear* last night I was able to get to [www.gmail.com](www.gmail.com), but no more!.......what's going on? :(

---

### Post by JohnPhys on 2007-03-03
This is really odd, I just did 

```
sudo apt-get install --reinstall firefox
```

*again*, and it fixed it for now, but this happened last night, and eventually the fix didn't work.

The only thing that I can think of is that I ran azureus after I tried that stuff, but I have no idea why that would interfere with anything.  Gaim and thunderbird have been running as well.

---

### Post by cogitordi on 2007-03-04
I am doubtful that Azureus has anything to do with it. But you could try it again just to eliminate the hypothesis. 

My Firefox 1.5.10 installation in Drake still doesn't work. I have another box running Eft/64 on which I compiled Firefox 1.5.10 - it doesn't have the problem we are discussing. This must be environmental. Something is not being maintained correctly.

---

### Post by JohnPhys on 2007-03-04
Yeah, I'll try to test some more things this afternoon.  Some other observations:

1.)  Getting to a secure site through a link from thunderbird did not work (car payment), however copying and pasting the link *did* work.  

2.)  Sites are currently working, as is the linking through thunderbird, but I have rebooted since the issues last arose, and I don't *think* I've run azureus yet.  Have you rebooted?  I know it's the last thing that you want to try with linux, but it *may* have fixed the problem with me.  There could have been some program accessing an older version of a library that got updated or some nonsense like that.

---

### Post by Blackneto on 2007-03-04
does anyone know if a bug report has been made?
This is insane, I reinstall, https works for a session then breaks again.

---

### Post by JohnPhys on 2007-03-04
I haven't filed one, simply because I'm not sure how to reproduce the bug effectively.

---

### Post by cogitordi on 2007-03-04
> **JohnPhys said:**
> I haven't filed one, simply because I'm not sure how to reproduce the bug effectively.

"Install Firefox 1.5.10 update" should be an adequate description. ;^)

Rebooting does nothing to solve the problem for me.

---

### Post by cogitordi on 2007-03-05
I completely removed Firefox from my Drake instance using Synaptic. Then I downloaded the Firefox 1.5.10 source and compiled it. I'm typing this now using 1.5.10 and I have been able to access all the encrypted sites.

I have not tried re-installing Firefox using Synaptic yet, but what I have done is prove that the problem has nothing to do with the code itself. There is some pre-existing condition on the affected computers.

---

### Post by JohnPhys on 2007-03-05
I'm not sure what you mean by ``preexisting'', since the error didn't occur until we installed that secound round of 1.5.10 updates.

---

### Post by Blackneto on 2007-03-06
well it seems to have ironed itself out.

I just followed the various ideas posted here and the problem is gone for now.
one other thing i did was install Epiphany to see what it was all about.
I don't know if that caused any change.

---

### Post by cogitordi on 2007-03-07
Using The Drake.

I compiled FF115 (STATIC) from source, built a tarball and can run the binary as expected, visiting all sites.

Using Synaptic, I did a complete removal of FF and Epiphany. I could still run the above static binary as expected.

I used apt-get to reinstall FF115. The installed package still cannot access https sites. The static binary works as expected.

There is no problem with the FF code (it compiles and runs). The pre-existing condition might be a problem with the package or with shared libraries already on disk.

Mozilla.com is ending support for FF 1.1.5 next month so I'm going to start using the FF 2.0.2 static build that I just compiled... and am testing here. :^)

---

### Post by rushcamera on 2007-03-07
I re-updated my Dapper box's Firefox to 10.5.0.10 today and yesterday's problem -- accessing email, https -- seems to have gone away.

---

### Post by nigol on 2007-03-08
A bug report have been filed.
See here:
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/90376](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/90376)

---

### Post by DJ_Peng on 2007-03-10
Actually, please consider upgrading to Firefox 2. The Firefox 1.5.x branch will get security and stability updates only through 27 April 2007. For more information see the [Mozilla Firefox 1.5.0.10 Release Notes]("http://www.mozilla.com/en-US/firefox/releases/1.5.0.10.html").

---

### Post by JohnPhys on 2007-03-10
DJ_Peng,

While Mozilla won't be giving out security updates for Firefox 1.5 after April 27th, I would think the Ubuntu developers would continue to backport patches applied to 2.0 to fix 1.5 security holes, much like they do with the older kernels used in all of the official Ubuntu releases.  I could be wrong about this though.

On another note, I haven't had the issue talked about in this thread for some time now, though it is frustrating since I'm not quite sure what it is I did that fixed it.

---

### Post by cogitordi on 2007-03-10
JohnPhys, I have not been able to duplicate your cure. I'm still using the Firefox 2 build that I created myself. 

I reinstalled Epiphany (which installs Firefox 1.5x in Drake) and I still cannot use it to access secure sites.

---

### Post by mdsmedia on 2007-03-13
I had the same problem with HTTPS sites. I installed the mozilla-psm package, as it had worked for others. Still the same problem. I reinstalled firefox using ```
sudo apt-get install --reinstall firefox
``` and it's now working properly.

---

### Post by cogitordi on 2007-04-01
I removed Epiphany and Firefox 1.5 from my Drake installation and am using Firefox 2.0.3 and Opera. Neither of the latter is having a problem.

---

### Post by cogitordi on 2007-04-03
> **JohnPhys said:**
> 
I would think the Ubuntu developers would continue to backport patches applied to 2.0 to fix 1.5 security holes, much like they do with the older kernels used in all of the official Ubuntu releases.  I could be wrong about this though.

I think it unlikely that anyone inside or outside the Mozilla Foundation is going to spend time applying changes made in the current codestream to an officially deprecated codestream. "Backporting" isn't straightforward work. I wouldn't want to do it, I wouldn't want to have my people doing it, and I see no advantage in doing it unless someone is going to pay someone big money to do it.

There is much more reason for everyone to pitch in to patch the Linux kernel than to keep an old (abandoned) version of a browser alive when there is a new version to replace it.

---

