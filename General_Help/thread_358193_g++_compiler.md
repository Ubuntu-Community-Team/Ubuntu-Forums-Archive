---
title: "g++ compiler"
date: 2007-02-10
forum: General Help
---

### Post by Rabbit_Alex on 2007-02-10
How can I install the g++ compiler for Ubuntu?  It isn't listed under the programming section in the Add/Remove applications menu.

Thank you

---

### Post by Mithrilhall on 2007-02-10
I see it when using apt-cache search via the console.

```
apt-cache search g++ | grep "g++"
```

---

### Post by Maestro23 on 2007-02-10
> **Rabbit_Alex said:**
> How can I install the g++ compiler for Ubuntu?  It isn't listed under the programming section in the Add/Remove applications menu.

Thank you

I found it thru Synaptic.  Possible you might have to enable some extra repositories if you are not seeing it.

How-To: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by Rabbit_Alex on 2007-02-10
I tried enabling the extra repositories using that guide, but it says I am not on the sudoers list.
How can I login as root to do this?

I am new to linux by the way.

---

### Post by gradedcheese on 2007-02-10
You should be in the sudoers list.  Take a look at "/etc/group" and make sure that your user name appears in the 'admin' group, like this:

```

admin:x:112:your_name_here

```

If it doesn't, you need to add it.  Without sudo you can't edit that file, but you can reboot into recovery mode and do it there.  You'll need to use a text-based editor to do it, I think people who are used to GUI stuff prefer 'pico' or 'nano'.  So:

pico /etc/group
(edit the file, save, exit)
shutdown -r now

Then when you boot up, run "sudo apt-get install build-essential"

---

### Post by TheWizzard on 2007-02-10
```
sudo aptitude install build-essential
```

---

### Post by Rabbit_Alex on 2007-02-12
> **gradedcheese said:**
> You should be in the sudoers list.  Take a look at "/etc/group" and make sure that your user name appears in the 'admin' group, like this:

```

admin:x:112:your_name_here

```

If it doesn't, you need to add it.  Without sudo you can't edit that file, but you can reboot into recovery mode and do it there.  You'll need to use a text-based editor to do it, I think people who are used to GUI stuff prefer 'pico' or 'nano'.  So:

pico /etc/group
(edit the file, save, exit)
shutdown -r now

Then when you boot up, run "sudo apt-get install build-essential"

Thank you gradedcheese.  It worked perfectly.  It's strange how I took myself out of the sudoers list though.

---

