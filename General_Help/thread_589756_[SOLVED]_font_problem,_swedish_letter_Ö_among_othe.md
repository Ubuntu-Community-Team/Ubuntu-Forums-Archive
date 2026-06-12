---
title: "[SOLVED] font problem, swedish letter Ö among other"
date: 2007-10-24
forum: General Help
---

### Post by mojoman on 2007-10-24
I did a clean install of Feisty about a week ago and for some reason the swedish letter Ö is not displayed properly in most (but not all) web pages. Below are two thumbnail, one from firefox on this forum where I typed in the letter Ö both in the google field and the forum search field (with blanks in front so there's no problem with spacing) and one from abiword. The latter is correctly displayed.

I've had a look at the settings under preferences but haven't made any headway. Generally speaking, my fonts are a bit smudgy and the sub-pixel rendering soesn't seem to do any good, especially on bold fonts. I've tried the hacks in[_ this thread_]("http://ubuntuforums.org/showthread.php?t=4456") but I can't really see any difference.

I've also installed libfreetype6 libcairo2 libxft2 and tested some different settings in the configuration but can't really see any difference.

I'm using fluxbox but also have Xfce4 installed.

Any ideas on how to fix this?
/mojoman

---

### Post by mojoman on 2007-10-25
I just noticed that the problem with the swedish letter Ö does not exist in swiftweasel so that at least it firefox-specific. It's still a problem for me, so ... *bump*

---

### Post by mojoman on 2007-11-06
Some more information. This is user-specific as I have another user where the Ö is properly displayed on the same system, using the same application.

Is there are way to set the firefox display settings back to default? That would probably solve it.

On a side note I might add that this probably occurred when I tried to get the fonts to be displayed crisp and sharp, something I have yet to managed under Ubuntu. Strangely enough, I got beautiful fonts under Debian. I've understood that it's usually the other way around but I found it quite easy to get very nice fonts in Debian.

/mojoman

---

### Post by Shimmy on 2007-11-06
Could it be a firefox-extension that causes the problem? Try to uninstall them all, or at least disable them.
I have never had any problems with my swedish chars.

---

### Post by mojoman on 2007-11-06
> **Shimmy said:**
> Could it be a firefox-extension that causes the problem? Try to uninstall them all, or at least disable them.
I have never had any problems with my swedish chars.

I tried disabling them just to be sure (the extensions I have are old but it's better to have it ruled out just the same), restarted firefox and the problem is still there.

Thanks anyway. Any more ideas?

/mojoman

---

### Post by Elena678 on 2007-11-06
hello, I also just installed my ubuntu system, but i don't have the problem, i am not so good in finding solutions, but so long as you are waiting you can use the web browser Opera, I think it is a a nice one, and it's made in the country next to us :P ones you use that, you won't go back :P.

okej, did you also tryed just to reinstall the firefox browser??

greetings

---

### Post by mojoman on 2007-11-06
> **Elena678 said:**
> hello, I also just installed my ubuntu system, but i don't have the problem, i am not so good in finding solutions, but so long as you are waiting you can use the web browser Opera, I think it is a a nice one, and it's made in the country next to us :P ones you use that, you won't go back :P.

okej, did you also tryed just to reinstall the firefox browser??

greetings

I can surf fine using FF, and even if I make searches using Ö (which appears fine in this text box but not in e.g. google's text box and also isn't displayed correctly in some pages) as the input is read correctly but displayed faulty.

Opera is a nice browser but that doesn't solve my problem. 

No, I haven't reinstalled FF since it works fine on other accounts on the same box and this strongly suggest that the fault is account-specific. Also, I use a 32-bit browser on a 64-bit system (Feisty Xubuntu) and removing and reinstalling might be something of a hassle (at least a little bit more than apt-get).

Thanks anyway.

Any other take on this problem?
/mojoman

---

### Post by Elena678 on 2007-11-06
okej, i am not sure, but i also only make a try with you.

you maybe just can change the default font.

you can change it in
Edit --> Preferences --> the tap content --> font & colors

I hope it make a difference for you

greetings

---

### Post by mojoman on 2007-11-06
> **Elena678 said:**
> okej, i am not sure, but i also only make a try with you.

you maybe just can change the default font.

you can change it in
Edit --> Preferences --> the tap content --> font & colors

I hope it make a difference for you

greetings

Tried that already but thanks anyway. I appreciate the effort.

/mojoman

---

### Post by Hallvor on 2007-11-06
Reinstall Firefox?

---

### Post by mojoman on 2007-11-07
> **Hallvor said:**
> Reinstall Firefox?

As I wrote in an earlier post, this is not only application specific but also user specific, which strongly suggest that this due to a faulty setting. However, I tried to remove and reinstall just to be sure and the problem persists. Now, I could probably fix this by deleting ALL configuration files to the specif account but as that would result in loss of other settings and god knows what else I'd rather not do that.

Any other ideas on this is much appreciated.
/mojoman
'

---

### Post by Shimmy on 2007-11-08
> rm -rf ~/.mozilla/firefox 
Should remove all your account specific settings, maby backup them first..

---

### Post by mojoman on 2007-11-08
I've been thinking along those lines but that would also remove my history, passwords, bookmarks and what else. Now, I could live with losing most of this but the bookmarks? Now, that hurts. One option could be to just back-up the bookmarks the remove the folder but I'd rather find the faulty setting.

---

### Post by mojoman on 2007-11-08
I did try removing the entire firefox-folder but the problem STILL persists. I'm at a total loss here. Come to think of it, when I boot up Debian on the same user, using the same /home-partition, do not have this problem. 

So, to recap: On Ubuntu one user have the problem and the other two have not, which implies that it is not system-specific but rather account-specific BUT the same user on the same /home-partition using Debian does not have the problem, which implies that the problem is OS-specific and not account-specific. I'm clueless.

/mojoman

---

### Post by mojoman on 2007-11-17
I deleted the folder ~/.fonts and that solved the problem (if that folder is absent, the default folder is used instead). Weird, since the same user used the same folder in Debian without the problems I had in Ubuntu but regardless of how, it took care of the problem.

/mojoman

---

