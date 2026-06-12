---
title: "ubuntu-6.06 and 6.10"
date: 2006-10-26
forum: General Help
---

### Post by fasoulas on 2006-10-26
I downloaded  ubuntu-6.06 a week ago and i was planning to install it on my pc but now i see that a newer 6.10 version has been released.

What's the difference of those two?

Can i avoid downloading the latest 6.10 version and still have what this version has on a 6.06v instalation???

PLs help me i am new on linux 
I am currenly using XP Home

---

### Post by taurus on 2006-10-26
Okay. here's the info on how to upgrade from Dapper to Edgy...

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by Kateikyoushi on 2006-10-26
Edgy is more advanced I would rather recommend it especially if you have newer hardware. You can update from 6.06 but things might go wrong and the update is about the same download as the iso.

What's new ? Read here. [LINK]("https://wiki.ubuntu.com/EdgyReleaseNotes")

---

### Post by fasoulas on 2006-10-26
Thnx for the ultra fast replie but what does this mean ???

>>>> This release will be supported for 18 months on both desktops and servers. Note that the previous stable release (6.06 LTS) is a long-term support release, and so users requiring a longer support lifetime may choose to continue using that version rather than upgrade to or install 6.10.

And if i update what does actually change?

---

### Post by beerfan on 2006-10-26
> **fasoulas said:**
> Thnx for the ultra fast replie but what does this mean ???

>>>> This release will be supported for 18 months on both desktops and servers. Note that the previous stable release (6.06 LTS) is a long-term support release, and so users requiring a longer support lifetime may choose to continue using that version rather than upgrade to or install 6.10.

And if i update what does actually change?

By "support" they mean that security bugs will continue to be released for the version. Perhaps it means something more which I am unaware of. What is important to note is that Ubuntu doesn't update the software in that release so if you're running Dapper Drake (6.06) for the next 5 years you'll be stuck with the same old versions of everything for that duration. If running modern software and current drivers is important then you'll want to install the latest release. Note that this is my perception as a relatively new Ubuntu user and not an expert.

---

### Post by luisg on 2006-10-26
Support time is how longer that specific release will have security and bug updates. LTS releases are targeted specially to business users and servers, where you don't expect to be version upgrading so often as home users.

Right now 6.06 is mature, and it's recommended for users going after stability before all. 6.10 is for those wanting latest version of software, possibly at the cost of some bugs.

---

### Post by BoomAM on 2006-10-26
Hi.
Does anyone know why Ubuntu isnt letting me upgrade?
Ive done the below command: 
```
gksu "update-manager -c" 
```
but it keeps erroring with: 
```
(gksu:6207): Gtk-WARNING **: cannot open display:
```

Any ideas?

Thanks in advance all. :)

---

### Post by taurus on 2006-10-26
Try replacing "gksu" with "gksudo"...

---

### Post by BoomAM on 2006-10-26
Same error, apart from the error number being '6824' this time.:confused:

---

### Post by taurus on 2006-10-26
You log into Gnome, right!!!

---

### Post by BoomAM on 2006-10-26
Of course im logged in!? How else would i access terminal?:confused:

---

### Post by BoomAM on 2006-10-26
Odd.
Ive just ran the same command in normal terminal, and this time it opens Update-Manager, checks for updates, closes, saying that there are none, then brings up the following error in terminal:
```
warnings.warn("apt API not stable yet", FutureWarning)
```

Im about an hour away from having downloaded the i386 iso, is there a command i can use to use that to update Dapper to 6.10 i686?

---

### Post by monoufo on 2006-10-26
There is a difference between a terminal you get inside gnome, and the real terminal.  The latter can be accessed by pressing ctrl-alt- and f1,f2,f3, or f4.  Graphical commands need to be run from inside gnome, at at least X.

the api warning is nothing.  It always does that, with no ill effects.


try running gksudo update-manager -c -d


if that doesn't work, change your /etc/apt/sources.list to edgy from dapper, run synaptic

gksudo synaptic

hit reload, mark all, and apply

---

### Post by BoomAM on 2006-10-26
> **monoufo said:**
> There is a difference between a terminal you get inside gnome, and the real terminal.  The latter can be accessed by pressing ctrl-alt- and f1,f2,f3, or f4.  Graphical commands need to be run from inside gnome, at at least X.

the api warning is nothing.  It always does that, with no ill effects.


try running gksudo update-manager -c -d


if that doesn't work, change your /etc/apt/sources.list to edgy from dapper, run synaptic

gksudo synaptic

hit reload, mark all, and apply
Same errors with the 'alt+ctrl+F1' approach.

I dont really want to have to do it the other way as it seems a bit bodged doing it like that.

Any ideas why its not working?

---

### Post by Boreras on 2006-10-26
won't
> sudo "sudo update-manager -c"
just do it?

if not try "sudo apt-get dist-upgrade"
and when done "sudo apt-get dist-upgrade" AGAIN (making a total of 2 times)

when it really doesn't work, and I recommend the other ways, as this could get a tipsy-bit messy.

"sudo gedit /etc/apt/sources.list"
and replace every "dapper" with "edgy", comment out all non-official links by placing a "#" in the beginning of that same line, save the file and "sudo apt-get update && apt-get upgrade".

if "sudo gedit /etc/apt/sources.list" gives an error try
"sudo nano /etc/apt/sources.list"
and replace every "dapper" with "edgy", comment out all non-official links by placing a "#" in the beginning of that same line, save the file and "sudo apt-get update && apt-get upgrade".

hope that helps.

if not…

---

### Post by jamesrose on 2006-10-26
:( :(  I am getting exactly the same problem.

---

### Post by BoomAM on 2006-10-26
Well, i did this command instead:
```
sudo sed -e 's/\sdapper/ edgy/g' -i /etc/apt/sources.list
```
inside a normal terminal window, then the below one, again, inside a normal terminal window:
```
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get dist-upgrade
```
And it did some stuff, said it had 800Mb or so of stuff to DL, and did i want to, i selected yes, and now its downloading away!
So asume that when its done downloading, it'll install, restart, and then i'll be using 6.10 with my preferences/programs from 6.06?

---

### Post by Boreras on 2006-10-26
remember that some source-sites from dapper drake won't work with edgy eft, even when replace dapper with edgy. So it probably is better to comment out those as well.

And maybe you'll have to add a "sudo apt-get update" before the 2nd apt-get dist-upgrade, but I'm not sure.

But doesn't dist-upgrade also change your sources.list? It should.

---

### Post by BoomAM on 2006-10-26
Well its still pulling all the data it needs off wherever at the moment. 
About 10-15mins to go according to the timer.
Hopefully it'll be a relativly painless process to do in regards to things not working.

---

### Post by BoomAM on 2006-10-27
It finished downloading, but then had an error at the end, a few seconds later, i get a message saying that theres updates, and to 'click here', so i did, it gave some error about some packages not being abled to update, like Abiword, then told me i have a further 165Mb of stuff to download.
I left it at that point and went out then, so i wondered what i should do now?

The two errors in terminal basically say that it failed to fetch 'fastjar' & 'libglade2'.

Should i close terminal, let update manager do its thing, then run the command that terminal suggests:
```
apt-get update *or* apt-get --fix-missing
```

Thanks in advance.

---

### Post by Ramses de Norre on 2006-10-27
> **Boreras said:**
> But doesn't dist-upgrade also change your sources.list? It should.

It absolutely shouldn't, dist-upgrade is not the same as upgrading to a new release, dist-upgrade does in fact the same as upgrade but it has permissions to remove and add packages in order to make newer packages work.

You need to change your sources.list when you want a new release.

Imaging that you would have got edgy alpha when you installed the new amarok from backports in dapper.. You wont have noticed it when using synaptic but you had to perform a dist-upgrade for that.

---

