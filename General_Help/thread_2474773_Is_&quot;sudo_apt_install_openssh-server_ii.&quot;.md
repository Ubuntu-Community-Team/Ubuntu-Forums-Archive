---
title: "Is &quot;sudo apt install openssh-server ii.&quot; malware (note the &quot;ii.&quot; at the end)"
date: 2022-05-07
forum: General Help
---

### Post by 777funk on 2022-05-07
I ran this command found online and the terminal started downloading all kinds of things for an hour or two. Something didn't seem right with the [COLOR=#ff0000]"ii."[/COLOR] at the end of this line:

```
sudo apt install openssh-server[COLOR=#ff0000] ii.[/COLOR]
```

Did I do something I shouldn't have to my computer?

---

### Post by magmon51 on 2022-05-07
According to this - [https://www.reddit.com/r/pop_os/comments/ijzt6t/what_is_the_difference_between_sudo_aptget/](https://www.reddit.com/r/pop_os/comments/ijzt6t/what_is_the_difference_between_sudo_aptget/) , you're just installing a lot of irrelevant packages due to "ii" being recognized as a separate string.

[sudo apt install openssh-server] should work just fine and ignore any superfluous packages!

---

### Post by 777funk on 2022-05-07
I wonder what "ii" is though... whatever it was it ran for a very long time before I killed the process.

---

### Post by GhX6GZMB on 2022-05-07
Don't run things you "find online". Bad idea.

---

### Post by TheFu on 2022-05-07
There is a meta-package called '**ssh**' which will install the ssh-server and ssh-client packages.  If you will put the ssh-server on the internet, please install a brute-force blocking tool too.

**sudo apt install ssh fail2ban**
is what I do on all my systems.  fail2ban will block brute-force attempts to ssh by default, though it can to much more.

---

### Post by deadflowr on 2022-05-07
ii is just an irc client
[https://packages.ubuntu.com/jammy/ii]("https://packages.ubuntu.com/jammy/ii")
But the issue here is you ran it with the period at the end which caused it to install all packages containing ii in their names.

---

