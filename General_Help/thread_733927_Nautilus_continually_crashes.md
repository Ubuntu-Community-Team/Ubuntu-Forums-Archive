---
title: "Nautilus continually crashes"
date: 2008-03-24
forum: General Help
---

### Post by xmastree on 2008-03-24
I'm having major problems since I upgraded to 7.10
Nautilus just crashes as soon as I try to do anything with it. I can open my home directory, but that's about it. I can't even navigate to another folder, since it just freezes up if I try.

Any ideas what could be causing this?

I've tried re-installing nautilus, but it didn't help.

---

### Post by Xyhthyx on 2008-03-24
Nautilus usually drops a text file in your home directory with debug information. If there is one, paste it here to help us find the root of the problem. Also, you could try clearing your ~/.nautilus directory.

---

### Post by xmastree on 2008-03-24
I can't see anything obvious in the home directory, but ~.nautilus has a few files, (named: saved-session-XXXXXX) the largest of which looks like:

```

<?xml version="1.0"?>
<session>
  <history>
    <bookmark name="chris" icon="user-home" uri="file:///home/chris"/>
    <bookmark name="Pictures" icon="gnome-fs-directory" uri="file:///home/chris/Pictures"/>
    <bookmark name="Music" icon="gnome-fs-directory" uri="file:///home/chris/Music"/>
    <bookmark name=".fonts" icon="gnome-fs-directory" uri="file:///home/chris/.fonts/"/>
    <bookmark name="Wheel" icon="gnome-fs-directory" uri="file:///home/chris/Wheel"/>
    <bookmark name="TIF" icon="gnome-fs-directory" uri="file:///home/chris/Wheel/TIF"/>
    <bookmark name="KINGSTON" icon="gnome-fs-directory" uri="file:///media/KINGSTON"/>
    <bookmark name=".fonts" icon="gnome-fs-directory" uri="file:///media/KINGSTON/.fonts"/>
    <bookmark name="SD-512" icon="gnome-fs-directory" uri="file:///media/SD-512"/>
    <bookmark name="oc0hx7kd.default" icon="gnome-fs-directory" uri="file:///home/chris/.mozilla/firefox/oc0hx7kd.default"/>
    <bookmark name="firefox" icon="gnome-fs-directory" uri="file:///home/chris/.mozilla/firefox"/>
    <bookmark name=".mozilla" icon="gnome-fs-directory" uri="file:///home/chris/.mozilla"/>
  </history>
</session>

```

Clearing those out made no difference.

---

### Post by xmastree on 2008-03-24
Some more info.

If I log in as a different user, it's fine.

If I log in as me, and run **nautilus /usr** from a terminal, it's fine until I go to my home directory. Then it spits the dummy.

So, *something* in my home directory is killing it...

Edit:

So, I copied everything from home into another directory, /chrisback/chris , ran **nautilus /chrisback**, opened chris and it died.
Now it's just a case of deleting things until it can be opened without dying...

---

### Post by xmastree on 2008-03-24
[SIZE="3"]**I seem to have nailed it! **[/SIZE]

There was one file, a simple .svg I had made with inkscape. Nautilus couldn't show a preview for some reason. Deleted it and all's well again.
[img]http://bestsmileys.com/happy/7.gif[/img]

Strange...

---

### Post by xmastree on 2008-03-24
Following up my own thread, but why not?

I remember now, I made that file not long before I upgraded. There was already a problem with the installation (lost the sound) and when nautilus started playing up I decided to start over completely.
Backed up everything important, including this file, and reinstalled.

The problems started when I restored my data... [img]http://bestsmileys.com/doh/2.gif[/img] And I didn't make the connection.

---

