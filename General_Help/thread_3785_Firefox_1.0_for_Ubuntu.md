---
title: "Firefox 1.0 for Ubuntu???"
date: 2004-11-09
forum: General Help
---

### Post by SVen2000 on 2004-11-09
Will Firefox 1.0 be availible via security upgrades of Ubuntu or will it only be availible as a part of the development snapshot?

As many bugfixes as it contains, it would be a good idea to make it availible soon for ubuntu, isn't it?

---

### Post by Julius on 2004-11-09
I have just untared Firefox 1.0 Final... no problems at all :D

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.5) Gecko/20041107 Firefox/1.0

mmm... I thought this was compiled earlier today... strange :S

---

### Post by flow on 2004-11-09
when will it be avaliable on the debian/ubuntu repos?
dont mind installing it manually but it would be nice to just use synaptic to upgrade it.

---

### Post by jdong on 2004-11-09
I somehow doubt the appearance of Firefox 1.0 in Warty.

---

### Post by mattyh on 2004-11-09
How 'bout in Hoary?  If not, then could someone explain how to replace the current firefox w/ firefox 1.0? Keeping all the functionality currently of course :)

---

### Post by flow on 2004-11-09
tried to find a repo with the new firefox.. latest was the 1.0pr..

[http://www1.apt-get.org/search.php?query=firefox&submit=&arch%5B%5D=i386&arch%5B%5D=all](http://www1.apt-get.org/search.php?query=firefox&submit=&arch%5B%5D=i386&arch%5B%5D=all) 

should i remove firefox(ubuntu build) 
and install firefox 1.0?

in synaptic, removing firefox involved ubuntu desktop which is not advisable right?

---

### Post by kastorff on 2004-11-09
[QUOTE=flow]in synaptic, removing firefox involved ubuntu desktop which is not advisable right?[/QUOTE]
ubuntu desktop is a meta package that ensures you've got everything you are supposed to...it can be removed if necessary without issue. Basically, anything that changes one of the packages ubuntu desktop incorporates will "break" it. It's scary until you understand how it works. 
 :D

---

### Post by HiddenWolf on 2004-11-09
It's an annoying package if you ask me.

I'd like to remove a lot of stuff, multiple programs that do the same thing etc, but I want to keep close to the default ubuntu, so I don't want to remove ubuntu-desktop.

And on-topic, yes, I think FF 1.0 final should be uploaded to warty.
It's got some improvements, and it'd help the FF movement.
I see FF growing as a sign on the wall for the MS monopoly, and thus feel like we should do anything to support FF.

Unlike OS in general, Firefox has managed to gain a momentum, and public awareness that can show the general public that there is something besides Microsoft.
Needless to say, Anything that puts Open Source on the frontpage, is good for linux, and thus good for us.

And no, I do not want to see the demise of Microsoft. I want to see them waking up and pushing for quality software, security and productivity.

---

### Post by flow on 2004-11-09
then what is the easiest/hassle free way to get firefox 1.0?
im not sure whether i should remove ubuntu desktop

---

### Post by flow on 2004-11-09
not sure whether its the easiest way. 
but i removed all the files from the /usr/lib/mozilla-firefox directory except the plugins folder and installed firefox to there..

---

### Post by daniels on 2004-11-09
[QUOTE=SVen2000]Will Firefox 1.0 be availible via security upgrades of Ubuntu or will it only be availible as a part of the development snapshot?[/QUOTE]It will absolutely not be available via the security channels -- as the name implies, that's only for security upgrades.  If you really, desperately want it and can't live with a preview release or whatever 0.93 was, I suggest upgrading to Hoary, which right now has 1.0PR, and will shortly have 1.0 final.  Note that barely enough time to build and upload a package has elapsed since the announcement, so expecting hoary packages nownownow is kind of unrealistic.

---

### Post by HungSquirrel on 2004-11-09
The preview release was version 0.10.  ;)

---

### Post by SVen2000 on 2004-11-09
[QUOTE=daniels] I suggest upgrading to Hoary, which right now has 1.0PR, and will shortly have 1.0 final. [/QUOTE]

So, it should be possible to install JUST firefox from the hoary - branch and let the rest remain as warty, is it?

what is the apt sources.list line for hoary?

---

### Post by HungSquirrel on 2004-11-09
Comment out your current sources.  Append the following to the bottom of the file:

```
 #Hoary
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted universe

deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ hoary-security main restricted
```

After an *apt-get update*, you should be able to install just Firefox.  Then you can comment out the Hoary entries, uncomment the Warty entries, and go on about your life with Warty.

At least, I assume so.

---

### Post by Julius on 2004-11-09
Doing that implies installing/updating a lot of packages... wouldn't it be easier to upload the .deb file from hoary to somewhere else? :P

---

### Post by krojc on 2004-11-09
@ daniels
Hmmm... That I do not understand. Maybe I did't read carefully througt Ubuntu Philosophy...
So until Hoary is released I will not be able to upgrade (except manually) to firefox 1.0?? In 6 month there will be 1.5 I guess, and still my warty will use 1.0. Please tell me I'm mistaken.

If I'm not then I don't understand Philosophy: first on big "gnome" release, and then quickly switch to unstable to follow small updates.

---

### Post by jdong on 2004-11-09
It's the same "philosophy" as most distros. After a version is released, don't make huge changes to it (like adding in new features & versions); hold those 'till the next release.

Warty's been released. Now, it's much more important to focus on securing Warty. Adding new packages (imagine splicing in X.org!) could cause major stability issues, not to mention different support procedures, for Warty. Having even a CHANCE of apt crapping out is a headache for system administrators.

When Hoary is released, it'll have the LATEST version of Firefox, whether that be 1.5 or 15.0. Same goes for other packages.

---

### Post by DyDx on 2004-11-09
Just get the regular Firefox 1.0 installer or tarball, install/extract it somewhere, and make a symlink to /usr/bin/firefox... works a charm.

---

### Post by jdong on 2004-11-09
I'd say that by the end of the week we'll get official Ubuntu .deb's for Firefox in Hoary. If you can wait that long, it's better to get the distro-customized version. Though usually the tarball will work, it won't "fit in" well with the rest of Ubuntu. If you look at the diff package for Ubuntu's Firefox ([http://archive.ubuntu.com/ubuntu/pool/main/m/mozilla-firefox/mozilla-firefox_0.99+1.0RC1-3ubuntu1.diff.gz](http://archive.ubuntu.com/ubuntu/pool/main/m/mozilla-firefox/mozilla-firefox_0.99+1.0RC1-3ubuntu1.diff.gz)), you can see many pages of changes the Ubuntu team has made to Firefox.

I don't have the free time tonight, but it may be possible to apply this patch to FF 1.0's tarball, but then again, if it's that easy, Ubuntu devs would have had the debs waay earlier than now!


Bottom line: cool it and wait!

---

### Post by RevJack on 2004-11-09
How does one upgrade to "Hoary?"

---

### Post by HungSquirrel on 2004-11-10
[http://www.ubuntuforums.org/showthread.php?t=2555](http://www.ubuntuforums.org/showthread.php?t=2555)

Be advised Hoary is an unstable development branch.

---

### Post by krojc on 2004-11-10
Guys I'm cool as an iceberg...

...but believe it or not I chose Ubuntu to be my production distro. I feel like I tried half of distros until I found this perfect and clean one, which fits like a glove and can be called "MY DISTRO". My "philosophy"  is stay stable and stay within borders to keep stable. This means that I didn't expect x.org updates, kernel updates, libblahblah, samba, but I surely expected 1.0 FF to replace 1.0 PR FF (which is final and not pre release) or thunderbird 1.0 to replace 0.8 (again stable for development) when it comes out, I expected openoffice, maybe gaim and of course security pathches which are obviously not problematic.

I hold developers responsible for my "pain" :) If you hadn't introduced synaptic and apt I'd be doing it manually wasting time and be quiet like I used to be, but no, you had to spoil me and now when I have the means I need to do it manually again?

But don't listen me bitching... rather we try to solve this.

Is it possible to add repository section for warty that would include USER apps from hoary that are not to dependent on new libs - like optional...?
(here I'm not alone - [http://ubuntuforums.org/showthread.php?t=3855&highlight=hoary](http://ubuntuforums.org/showthread.php?t=3855&highlight=hoary))

Will FF 1.0 be in universe? (I actually had not enabled it, yet)
Where is two panel file manager for ubuntu-gnome :)  - don't take this seriously

What I found is perfect and I'm not letting go. What I want to say is, get used to my complaining... in the end I expect doing it manually again.

Keep up, Ubuntu!

---

### Post by jdong on 2004-11-10
Unfortunately, Hoary's repos aren't designed that way.

Maybe what you were talking about is what the warty-updates section is for. A dev will have to answer that one. In a way, I do agree with you.

On the other hand, look at Debian Stable, Redhat EL, or SuSE. They all use the same policy, but they only make annual releases. Debian only makes releases every 3+ years! Look at what version of Mozilla is in Woody.


Count yourself fortunate that Ubuntu already makes bi-yearly releases.

---

### Post by daniels on 2004-11-10
Firefox 1.0 will come to Hoary.  The developer responsible for Firefox is on a one or two day short holiday (which he definitely deserves), but has already been looking at Firefox.  So chill.

The reason it's not as simple as just updating it is that we tried that with 0.93->1.0PR, and then we found that it segfaulted every time it tried to open a JavaScript popup window.  The quality of the release is an absolute unknown, and thus we'd rather stick with a known quantity than something which has seen lots of random changes since its preview, with an unknown effect.  That being said, there are no new features that I know of since 1.0PR, so it really isn't much different to what you're already using.

As for warty, our policy on releases is clear.  If it doesn't fix security, it's not going in.  If you're convinced that you'll die without bleeding edge Firefox, use Hoary.

---

### Post by daniels on 2004-11-10
[QUOTE=HiddenWolf]It's an annoying package if you ask me.[/QUOTE]But essential for upgrades.  Without, there's no way to say 'OK, a base Ubuntu desktop should contain xserver-xorg, so go and remove that instead of keeping xserver-xfree86 around'.  You cannot design a sane upgrade path without it.

> And on-topic, yes, I think FF 1.0 final should be uploaded to warty.
It's got some improvements, and it'd help the FF movement.
I see FF growing as a sign on the wall for the MS monopoly, and thus feel like we should do anything to support FF.We are supporting Firefox with the inclusion of it in both Warty and Hoary, and as the default browser.  Having 1.0 final in Warty through 'security' channels (?!?) will not help any.

---

### Post by jdong on 2004-11-10
[QUOTE=daniels]But essential for upgrades.  Without, there's no way to say 'OK, a base Ubuntu desktop should contain xserver-xorg, so go and remove that instead of keeping xserver-xfree86 around'.  You cannot design a sane upgrade path without it.

We are supporting Firefox with the inclusion of it in both Warty and Hoary, and as the default browser.  Having 1.0 final in Warty through 'security' channels (?!?) will not help any.[/QUOTE]

Not to sound imprudent or disrespectful... I'm quite neutral on this issue...

But what is the **warty-updates** channel for?

---

### Post by daniels on 2004-11-10
[QUOTE=krojc]So until Hoary is released I will not be able to upgrade (except manually) to firefox 1.0?? In 6 month there will be 1.5 I guess, and still my warty will use 1.0. Please tell me I'm mistaken.[/QUOTE]Not if you're using Warty, which is a designated stable (as opposed to development) release.  Warty is the same *known* *quantity* (new bugs don't just appear -- either they've always been there, or they haven't), plus security fixes.  It is not a moving target, and none of our releases ever will be.

> If I'm not then I don't understand Philosophy: first on big "gnome" release, and then quickly switch to unstable to follow small updates.If you want to track the bleeding edge after our release, then ... switch to the bleeding edge component, yes.

---

### Post by daniels on 2004-11-10
[QUOTE=jdong]Not to sound imprudent or disrespectful... I'm quite neutral on this issue...

But what is the **warty-updates** channel for?[/QUOTE]Being separate from security -- AIUI it is for *critical* updates (e.g. this package does not work at all), not dissimilar to Debian's stable updates.  Except in that we'll have another stable release in April.

---

### Post by jdong on 2004-11-10
[QUOTE=daniels]But essential for upgrades.  Without, there's no way to say 'OK, a base Ubuntu desktop should contain xserver-xorg, so go and remove that instead of keeping xserver-xfree86 around'.  You cannot design a sane upgrade path without it.

We are supporting Firefox with the inclusion of it in both Warty and Hoary, and as the default browser.  Having 1.0 final in Warty through 'security' channels (?!?) will not help any.[/QUOTE]

Not to sound imprudent or disrespectful... I'm quite neutral on this issue...
But what is the **warty-updates** channel for? Currently, cdrecord and mkisofs updates are in that repo....

---

### Post by jdong on 2004-11-10
ok, thanks. That's making sense now. Out of curiousity, what's the story behind the new cdr tools?

---

### Post by daniels on 2004-11-10
[QUOTE=jdong]ok, thanks. That's making sense now. Out of curiousity, what's the story behind the new cdr tools?[/QUOTE]'Now that I have time to breathe, I can do it,' is the story in a nutshell. :)

---

### Post by krojc on 2004-11-10
I'm chilled...

I understand and accept what you all say, but it bothers me because it seems that dpkg -i works in a bit unnatural way. If I install deb package using dpkg and installaton is not successfull it tells me what dependencies are, but in the same time it installs the package and apt or synaptic show it as broken.

Using repositories that does not happen.
Using hoary repos wants to upgrade all the packages.

What I had in mind was creating a section of HOARY where these USER apps would reside. I could add repository "hoary apps" and update these packages + deps to latest non system apps at my will.

But it still does not matter. I already made peace with the idea that I'll have to dig in manually.

---

### Post by uggeli on 2004-11-10
[QUOTE=daniels]
As for warty, our policy on releases is clear.  If it doesn't fix security, it's not going in.  If you're convinced that you'll die without bleeding edge Firefox, use Hoary.[/QUOTE]

Hmm isn't there security updates in Firefox 1.0 for tabbed browsing, or was that problem only in windows versions?

---

### Post by jdusablon on 2004-11-10
Forgive my ignorance, but what are the real advantages to Firefox 1.0 Final versus 1.0PR and 0.93? I hope it's in-app support for extensions and 3rd party plug-ins.

---

### Post by nuopus on 2004-11-10
[QUOTE=HiddenWolf]It's an annoying package if you ask me.

I'd like to remove a lot of stuff, multiple programs that do the same thing etc, but I want to keep close to the default ubuntu, so I don't want to remove ubuntu-desktop.

And on-topic, yes, I think FF 1.0 final should be uploaded to warty.
It's got some improvements, and it'd help the FF movement.
I see FF growing as a sign on the wall for the MS monopoly, and thus feel like we should do anything to support FF.

Unlike OS in general, Firefox has managed to gain a momentum, and public awareness that can show the general public that there is something besides Microsoft.
Needless to say, Anything that puts Open Source on the frontpage, is good for linux, and thus good for us.

And no, I do not want to see the demise of Microsoft. I want to see them waking up and pushing for quality software, security and productivity.[/QUOTE]
 Removing ubuntu-desktop will not ruin your the default "setup" of the OS. It is basically just a list of applications that make the install easier.

Its kind of like shopping .... you use the shopping list to help you get the food, but when your done putting all the food in your car after paying for it ... you don't need the list anymore. Or do you? Well ... I guess if you want to keep to the default shopping list! LOL

---

### Post by nuopus on 2004-11-10
[QUOTE=jdusablon]Forgive my ignorance, but what are the real advantages to Firefox 1.0 Final versus 1.0PR and 0.93? I hope it's in-app support for extensions and 3rd party plug-ins.[/QUOTE]
 Over 250 bug fixes! Havent found any new features yet ... although I just removed the package with apt-get and downloaded the installer from the firefox web site. Its easy ... the installer walks you through it.

Just choose /usr/lib/mozilla-firefox as your install path and link firefox to /usr/bin. (ln -sf /usr/lib/mozilla-firefox/firefox /usr/bin)

---

### Post by jdong on 2004-11-10
What'll happen is that security bugfixes in 1.0 final will be backported to 0.9.3 and patched onto Ubuntu's Firefox, then placed in security as a revision -- if the flaws are major enough to warrant this.

---

