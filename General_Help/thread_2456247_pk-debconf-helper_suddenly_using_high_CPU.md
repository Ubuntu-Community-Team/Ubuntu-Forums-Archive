---
title: "pk-debconf-helper suddenly using high CPU"
date: 2021-01-07
forum: General Help
---

### Post by &amp;KyT$0P# on 2021-01-07
I noticed lately that after the last few times I've run software updates on apt packages, my computer's fans were kicked up for maybe ~30 seconds after the update had completed.  This time I caught the process causing it: [FONT=Courier New]pk-debconf-helper[/FONT].

Searching shows that it is part of PackageKit and I am not alone in having this problem.  But, what puzzles me is, I could swear this was **_not_** happening before this new year. :-k

I looked into purging PackageKit, but the collateral from that would be unacceptable.

What changed this year that PackageKit is now consuming significant CPU?  How to get my PackageKit back to how it was in 2020, i.e. not using excessive-seeming resources, without uninstalling PackageKit or breaking the programs that declare it as a dependency (software-properties-gtk, [FONT=Courier New]add-apt-repository[/FONT], Muon package manager)?

---

### Post by &amp;KyT$0P# on 2021-01-10
bump

---

### Post by #&amp;thj^% on 2021-01-10
h2 longtime, see if this is acceptable then:
```
systemctl stop packagekit
```
And:
```
systemctl mask packagekit
```

removing packagekit will unfortunately remove a bunch of other things if you have gnome installed. Masking it will remove the autoupdate... supposedly.
I seen it on 18.04 and this worked as needed. Let me know if this acceptable. :)

---

### Post by &amp;KyT$0P# on 2021-01-10
Hi 1fallen, nice to see you around and thanks for pointing me to use systemctl.  I ran the commands you suggested, plus
```
$ systemctl --user stop pk-debconf-helper{,.socket}
$ systemctl --user disable pk-debconf-helper{,.socket}
$ systemctl --user mask pk-debconf-helper{,.socket}
$ sudo systemctl stop packagekit-offline-update
$ sudo systemctl mask packagekit-offline-update
```

Quick check did not find any loss of functionality of the software I have that depends on PackageKit.

My software is up to date at the moment, so might be a few days before I can report back.

---

### Post by &amp;KyT$0P# on 2021-01-12
The above didn't completely disable PackageKit.  I was getting errors in syslog.

To prevent the errors, I also needed to comment out the contents of [FONT=Courier New]/etc/apt/apt.conf.d/20packagekit[/FONT] .  And with that, doing a software update did not result in high CPU use afterwards.

I still can't shake wondering why none of this was necessary in 2020, but it seems back to being good now and I can't be bothered to investigate this further at the moment.

Thanks 1fallen for your help!

---

