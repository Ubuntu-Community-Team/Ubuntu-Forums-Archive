---
title: "How do I issue the command &quot;upgrade all except google-chrome-stable&quot;?"
date: 2014-07-18
forum: General Help
---

### Post by rdh61 on 2014-07-18
Hi,

After doing "sudo apt-get update", how do I issue the command "upgrade all except google-chrome-stable"?

Many thanks.

---

### Post by Dennis N on 2014-07-18
Before running apt-get upgrade, put the package you don't want upgraded on hold.

See [https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)
Maintainance Commands, #9.

For an example, see: [http://administratosphere.wordpress.com/2011/07/13/putting-debian-packages-on-hold/](http://administratosphere.wordpress.com/2011/07/13/putting-debian-packages-on-hold/)

Run apt-get upgrade and the package on hold won't show to be upgraded.

---

### Post by Lars Noodén on 2014-07-18
If the exact name of the package is "google-chrome-stable" then one way is like this:

```

echo "google-chrome-stable hold" | sudo dpkg --set-selections

```

Or if you have synaptic, you can highlight the application name then go to the menu Package->Lock Version

A second way would be to use apt-pinning but that is a little more complex to set up.

Either way you lose out on security and functional updates.

Edit:  oops, too slow

---

### Post by rdh61 on 2014-07-18
Thank you to both. That is what I needed.

But...

> **Lars Noodén said:**
> 
Or if you have synaptic, you can highlight the application name then go to the menu Package->Lock Version


My problem was, I did this, but then used the terminal to upgrade (sudo apt-get upgrade), which overrode the lock in Synaptic and the package was upgraded anyway.

---

### Post by Lars Noodén on 2014-07-18
What is the package status?

```

dpkg --get-selections google-chrome-stable

```

It should be "hold".

---

### Post by rdh61 on 2014-07-18
Now it is indeed "hold", after following your and Dennis N's advice.

---

