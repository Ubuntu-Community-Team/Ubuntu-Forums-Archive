---
title: "Spell Checking in Ubuntu 14.04"
date: 2014-10-18
forum: General Help
---

### Post by kpfuser on 2014-10-18
When I post in Ubuntu Forums, there appears to be no spell checking available. The same appears to be the case when I create a text document using gedit. However, when I create a new document using LibreOffice Writer, spell checking becomes available. What do I need to do to avail myself of spell checking when I post in the forum or type documents in gedit?

---

### Post by bapoumba on 2014-10-18
For the forums, it is related to your browser. Which one are you using ?
I have not used gedit in a long while. May be here :
[https://help.gnome.org/users/gedit/stable/gedit-spellcheck.html.en](https://help.gnome.org/users/gedit/stable/gedit-spellcheck.html.en)
[https://help.ubuntu.com/community/gedit](https://help.ubuntu.com/community/gedit)

---

### Post by kpfuser on 2014-10-19
bapoumba,

Thanks for your reply.

The browser I use is Firefox 33 (Mozilla Firefox for Ubuntu canonical - 1.0), i.e. the default browser of  the desktop version of 14.04

Gedit does not seem to find much favor with other 14.04 users as well. I use it because it is the default text editor of 14.04. Perhaps you could suggest an alternative simple text editor that features spell checking by default so as to circumvent this shortcoming of gedit.

---

### Post by Bashing-om on 2014-10-19
kpfuser;

Can not help a bunch about spell checking in 'gedit' ( dictionaries are installed, right ?)l but, for the browser:
in a post reply box, right click and choose "spell-checker options" and set as appropriate to your language/usage.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by mc4man on 2014-10-19
Pretty much all new installs (at least those done with Internet disconnected) will require setting the  Language in Firefox once.

As far as gedit  - 
shift+F7
or
tools > Check Spelling...

---

### Post by kpfuser on 2014-10-20
Thank you all!

Finally things have fallen into place. Following Bashing-om's suggestion, namely

> for the browser: in a post reply box, right click and choose "spell-checker options" and set as appropriate to your language/usage

produced the hoped-for result as far as getting spell checking for forum posts, after selecting the respective language (English (US)) first and then installing the corresponding dictionary.

Next for gedit following  mc4man, i.e.

> As far as gedit -
shift+F7
or
tools > Check Spelling... 

did the job via Tools --> Set Language... at first and subsequently Tools --> Check Spelling... when needed.

What remains a mystery still is why the language selection and the addition of the respective dictionary did not take place automatically during installation for both firefox as well as gedit since the internet connection was active and the language was set to english (US) early on during installation. To be sure, I used a 12.04 installation DVD (rather than an unreadable 14.04 one) and followed the 12.04 installation with an immediate upgrade to 14.04. However, this offers little by way of explanation to me since spell checking in firefox/gedit was not available in 12.04 either thus raising the same question in this case as well.

---

### Post by mc4man on 2014-10-20
As far as Firefox this has been going on for about 3 yrs. (it initially was worse, then each new firefox upgrade lost the language. Now it seems just on first install.
Had a bug, went nowhere - 
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/894085](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/894085)

---

### Post by bapoumba on 2014-10-21
Just to add, same here with FF. Even with a language selected in Prefs > Content, I have to do it every time I open a new FF instance after booting up. Most probably because I wipe stuff on FF closing, but I have not investigated further.

---

### Post by kpfuser on 2014-10-21
Thank you gentlemen for your comments. It seems that I must go through language selection and dictionary installation after every new FF installation. In my case, the changes made to FF in this respect last persisted so far. So I'll say "Thank God for small favors" and hope for the best in the future.

---

