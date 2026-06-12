---
title: "modifying variables with sed, gconf --direct --input"
date: 2006-12-26
forum: General Help
---

### Post by summersab on 2006-12-26
I've been all over the internet and I'm still having trouble. Here's what I'm trying to do. Actually, I have two things I want to do. Number 1. I'm trying to modify a gconf list (string type) using gconftool-2 and sed. Here is what I have so far:

# Sets variable value to list values.
value=$(gconftool-2 --get /apps/panel/general/applet_id_list)

## need some sed operation to change the string, eg
value=$(sed 's/'\]'/',deskbar\]'/g' $value) which would add "deskbar" to the end of the string list

# Adds the new string to the proper location in gconf
gconftool-2 --set --type list --list-type string /apps/panel/general/applet_id_list $value

**Pretty much, my question is simple: how do you modify a local bash variable using sed? I cannot figure it out for the life of me!!!

Alright, my second question. I know how to gconftool-2 --dump stuff to xml files. However, how do I add those files back into gconf? Ideally, I want to make the settings systemwide for all users. So far, I know this:

gconftool-2 --direct --config-source xml:readwrite/*some location* --load /*my xml file*

What location do I use? I tried the following:
/etc/gconf/gconf.xml.defaults
/etc/gconf/gconf.xml.mandatory
/etc/gconf/2/local-mandatory.path
/etc/gconf
$(HOME)/.gconf
~/.gconf
/home/$user/.gconf

I also tried everything that is in /etc/gconf/2/path. Everything I try, I CANNOT get the settings to load into gconf when I look at gconf-editor to see if the changes were applied. Where do I put the keys?

Thanks for your help. If there is a better way to do what I'm trying to do, please tell me. If there is a better forum for my post to go (whether Ubuntu or another more technical site), tell me as well.

---

