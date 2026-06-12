---
title: "update manager/archive"
date: 2013-08-01
forum: General Help
---

### Post by frogeyedan on 2013-08-01
trying to run an update i get this error:
n unresolvable problem occurred while initializing the package information.


Please report this bug against the 'update-manager' package and include the following error message:


'E:Encountered a section with no Package: header, E:problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'


thisw is 12.04 precise 64 bit kernel 3.5-36-generic
gnome 3.4.2 ( with unity, flux and openbox installed)

So basically it wont let me update because of an update manager problem.  
has anyone had this issue?  does that archive name look flawed?
than ks for any insight!
Dan

---

### Post by frogeyedan on 2013-08-01
ummm    smiley face = :    P  with no spaces...

---

### Post by Bashing-om on 2013-08-01
frogeyedan; Hi !

Let's try and fix that package list.
Do terminal codes:
```


sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade

```
As an absolute beginner, research commands prior to blind acceptance; do: Terminal commands:
```
man rm
man mkdir
man apt-get

``` for confidence and assurance.

[INDENT][INDENT]should workie great last long time
[/INDENT][/INDENT]

---

### Post by frogeyedan on 2013-08-01
it did indeed work.  my dog is now your friend for life....

---

### Post by Bashing-om on 2013-08-02
frogeyedan;

Good deal .. glad ya back up and running strong.

Please mark this thread "solved" from the thread tools option.

And I did get a chuckle in reference to your dog !

[INDENT][INDENT]all's well that ends well[/INDENT][/INDENT]

---

