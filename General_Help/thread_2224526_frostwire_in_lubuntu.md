---
title: "frostwire in lubuntu"
date: 2014-05-16
forum: General Help
---

### Post by skout2 on 2014-05-16
Has anyone sucessfuly installed frostwire in lubuntu? If so, how did you get it to connect?

---

### Post by gubatron on 2014-07-16
what issue are you having exactly?

installation should be as simple as using the [frostwire-5.3.4.all.deb]("dl.frostwire.com/frostwire/5.7.4/frostwire-5.7.4.all.deb") file.

**sudo dpkg -i frostwire-5.7.4.all.deb**

you can also use gdebi

**sudo gdebi frostwire-5.7.4.all.deb**

Then from your console, (and also from your internet app launcher sub menu you should see the frostwire icon), just type

frostwire

and it should open and connect.

If it is not connecting you might want to check your firewall settings to make sure FrostWire can open and listen to incomming connections.

If you are able to run it, and it's not connecting, it'd be awesome if you'd paste here all the output you get on your terminal, I might be able to help.

Source: FrostWire Developer

---

