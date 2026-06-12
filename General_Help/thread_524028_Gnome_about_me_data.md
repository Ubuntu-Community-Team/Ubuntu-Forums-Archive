---
title: "Gnome about me data"
date: 2007-08-12
forum: General Help
---

### Post by panther_sn on 2007-08-12
Hi I am trying to find out where I would find the data from the Gnome About Me Panel.

I asked this question and was given a really quick response which was great, but I was told in /etc/passwd and there is information there but not what I was after, as I am trying to find where it would actually store the things that are stored in there, like if I have put my email address or phone number in that panel where it is stored.  Thanks any help would be appreciated.

Thanks Panther

---

### Post by Juffo-Wup on 2007-08-12
*grep, give me sight beyond sight!*

After putting some weird input in my own profile and the searching with [grep]("http://en.wikipedia.org/wiki/Grep") my home directory to find it, I'm pretty sure that the file you are looking for is /home/$YOU/.evolution/addressbook/local/system/addressbook.db, as it always showed up as the only (early) finding.

But it says that the file is binary, though.

I hope this helps.

Edit: there is no space in "add resbook".

---

### Post by panther_sn on 2007-08-12
Thats awesome thankyou very much, Do you happen to know if there is a way to read the addressbook.db file as when I check the addressbook in Evolution, it still doesn't show up with the info that I have put in there using "about me"  So I am wondering what sort of format it has been put in as

---

### Post by Juffo-Wup on 2007-08-15
Sorry for the delay.

Well, I don't know if you have found a (better) solution already, but opening the file in a plain text editor (but not Gedit, I think) can show you the info... alongside a lot of gibberish.

I know this works with some command line editors such as nano and vim (or gvim), or maybe even [less]("http://en.wikipedia.org/wiki/Less_%28Unix%29"), if you just want to view it.

---

