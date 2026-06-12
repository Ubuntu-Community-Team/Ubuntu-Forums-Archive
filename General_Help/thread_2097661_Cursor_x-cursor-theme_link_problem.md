---
title: "Cursor x-cursor-theme link problem"
date: 2012-12-24
forum: General Help
---

### Post by MrGrey1 on 2012-12-24
Not sure how I've borken this but... 
I was mucking around trying to get my cursor theme to work consistently. I had the theme working except when the system wait animation was running it would drop back to default. I tried following this 
[http://rc98.net/mousecursor](http://rc98.net/mousecursor)
and somehow I have managed to accidently link
x-cursor-theme -> /etc/alternatives/x-cursor-theme
in /etc/alternatives/
This is obviously recursive and wrong, it links to istelf, so I removed the link and reapplied the default link

sudo ln -sf /usr/share/icons/DMZ-White/cursor.theme /etc/alternatives/x-cursor-theme

ls -la showed the new link correctly. HOWEVER, I tried running 
sudo update-alternatives --config x-cursor-theme

and got this error 

update-alternatives: using /usr/share/icons/DMZ-Black/cursor.theme to provide /etc/alternatives/x-cursor-theme (x-cursor-theme) in manual mode
update-alternatives: error: unable to install `/etc/alternatives/x-cursor-theme.dpkg-tmp' as `/etc/alternatives/x-cursor-theme': No such file or directory

Now looking back at /etc/alternatives the broken recursive link is back!
I have expermineted exstensivly with this and no matter what I try I can't seem to get rid of this recursive link. It always regenerates itslef... help! How do I remove or reset this link or find out how it is being recreated?

Edit: this now seems to have broken compiz as well... getting no windows borders and compiz crashing frequently... because I tried to change a cursor? ./sigh.
Looks like my whole system is falling apart now. File manager not working and most applications crashing. Looks like im fubar.

---

