---
title: "Want to run a terminal command by double-clicking an icon"
date: 2008-06-19
forum: General Help
---

### Post by mjpatey on 2008-06-19
Hi,

How do I run some terminal code by double-clicking on an icon?  The command I'm trying to do this with is:

```
sudo setpci -s 00:02.1 f4.b=ff
```(WARNING:  Please don't type this in your own system, as I have no idea what it will do!  On my Asus EeePC 900, it sets the screen to super-bright for outdoor viewing.)

I've tried:

1. Create a launcher on the Desktop, and the command to launch is the above code.
2. Create a text file containing the code and save it with a .sh extension, setting it as executable, and running it by typing "sh superbright.sh"
3.  The same as #2, but removing the "sudo" from the text file, and then I create a launcher that contains "gksudo sh ~/superbright.sh"

None of this works.  It all seems like it should, to me.  How do I accomplish this?  Thanks for any light you can shed!

-Mark

---

### Post by ad_267 on 2008-06-19
You need to replace sudo with gksudo.

So make a launcher with:
```
gksudo setpci -s 00:02.1 f4.b=ff
```

Edit: Thought I should explain why #3 doesn't work. When you run sudo you are effectively becoming the root user. The root user has a home directory at /root, so it's looking for the script in /root/superbright.sh, not in your home directory.

---

### Post by sdennie on 2008-06-19
I have a script that does something vaguely similar and I run it with:

```

gksudo sh /home/my_username/bin/name_of_script.sh

```

Your problem may simply be that ~ may not be resolving properly and you need to use the explicit path.

---

### Post by ad_267 on 2008-06-19
> **vor said:**
> Your problem may simply be that ~ may not be resolving properly and you need to use the explicit path.

~ is resolving to /root, your home directory when you are root.

---

### Post by mjpatey on 2008-06-19
Hm... I tried that, and it doesn't cause the screen to go bright.  Just to make sure I didn't mess anything up, I tried entering the code manually in a terminal, and it worked fine.

It's perplexing!

---

### Post by mjpatey on 2008-06-19
...an addendum to post #5... I double-click the launcher that includes the gksudo command, and it asks for my password, which dims the screen during entry.  When the screen comes back up after I've entered the password, it's only at normal brightness... could the fact that this command plays with screen brightness be the reason it's not working (as the screen brightness is being manipulated by X during the sudo command)?

---

### Post by sdennie on 2008-06-19
No, I think that dimming is done by changing the gamma correction and not by changing brightness.

---

### Post by ad_267 on 2008-06-19
Try it with the script
ie
```
gksudo sh /home/user_name/superbright.sh
```

---

### Post by mjpatey on 2008-06-19
ad_267, it worked!  Thanks for sticking with me on that.  I was pretty sure I'd tried it already along with the other combinations, but I guess not.

Thank you!

-Mark

---

### Post by ad_267 on 2008-06-19
You should probably thank vor, that was his original suggestion. I'm not sure why it makes a difference when it's run in a script.

---

