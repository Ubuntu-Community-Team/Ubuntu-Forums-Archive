---
title: "Trouble with Webmin installation"
date: 2013-11-24
forum: General Help
---

### Post by MarcusL on 2013-11-24
Hi all,
I am reasonably new to Ubuntu, and have run into trouble installing Webmin. I followed the instructions in [this link]("http://joelmccune.com/2012/10/26/install-webmin-on-ubuntu-12-04-server/") and I am getting the following errors at the command: 

```
[COLOR=#333333][FONT=Monaco]
sudo apt-get install webmin
[/FONT][/COLOR]
```

It says back to me:
```
root@LSERVER:/root# sudo apt-get install webmin
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

```

Any ideas / suggestions welcome. Thanks

---

### Post by Bashing-om on 2013-11-24
MarcusL; Hi !

This error often indicates a corrupted/inconsistent control file;
Try this:
Terminal codes;
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade

```
Where "apt-get update" will rebuild the index files, and -upgrade- will update the installed packages.

Then try and install "webmin" once more.

Please advise on results !

[INDENT][INDENT]ain't noth'n but a thing
[/INDENT][/INDENT]

---

### Post by MarcusL on 2013-11-24
Hi Bashing-om, GENIUS! It worked perfectly. Many thanks!!

---

### Post by Bashing-om on 2013-11-24
MarcusL; Good deal !

No genius too it (thanks though), seen that one many times. When the index files are in an inconsistent state, that is the 1st thing to do !

As all is now in good stead, please mark this thread as solved - 1st post -> thread tools - as that aides others seeking a similar solution and as well helps keep the forum tidy.

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

