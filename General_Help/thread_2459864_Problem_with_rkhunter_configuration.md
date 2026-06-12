---
title: "Problem with rkhunter configuration"
date: 2021-03-28
forum: General Help
---

### Post by krane1230 on 2021-03-28
Hello,

I ran ```
sudo apt install rkhunter -y
``` and installed rkhunter. I am trying to configure it with ```
vim /etc/rkhunter.conf
```, but I get this:
```








E325: ATTENTION
Found a swap file by the name "/etc/.rkhunter.conf.swp"
          owned by: root   dated: Mon Mar  8 12:53:50 2021
         file name: /etc/rkhunter.conf
          modified: YES
         user name: root   host name: Lenovo-ideapad-110-17IKB
        process ID: 30094
While opening file "/etc/rkhunter.conf"


(1) Another program may be editing the same file.  If this is the case,
    be careful not to end up with two different instances of the same
    file when making changes.  Quit, or continue with caution.
(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/rkhunter.conf"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/etc/.rkhunter.conf.swp"
    to avoid this message.


Swap file "/etc/.rkhunter.conf.swp" already exists!
[O]pen Read-Only, (E)dit anyway, (R)ecover, (D)elete it, (Q)uit, (A)bort: 



```
How can I fix this and configure rkhunter? I used these 2 guides:
[https://kifarunix.com/how-to-install-rkhunter-rootkit-hunter-on-ubuntu-18-04/](https://kifarunix.com/how-to-install-rkhunter-rootkit-hunter-on-ubuntu-18-04/)
[https://success.trendmicro.com/solution/1113864-editing-configuration-files-of-linux-based-products](https://success.trendmicro.com/solution/1113864-editing-configuration-files-of-linux-based-products)

---

### Post by ActionParsnip on 2021-03-28
Run:
```

sudo rm /etc/.rkhunter.conf.swp

```

---

### Post by krane1230 on 2021-03-28
> **ActionParsnip said:**
> Run:
```

sudo rm /etc/.rkhunter.conf.swp

```
I found another way to install rkhunter, marking as solved

---

### Post by HermanAB on 2021-03-28
OK, though the problem of rkhunter being essentially useless remains...

---

### Post by TheFu on 2021-03-28
> **HermanAB said:**
> OK, though the problem of rkhunter being essentially useless remains...

But that's a problem for the rkhunter team - fixing an essentially useless tool. I'm sure it isn't really useless, but harder to configure to prevent all the false and un-useful output.

That team needs to read *The Unix Philosophy*.
[LIST]
[*]When things work as expected, don't say anything.
[*]When something fails, complain loudly.
[/LIST]
I always found all the rkhunter output overwhelming for saying way too much when everything was fine, except 1 tiny, false positive.

IMHO.

If I'm searching for a root-kit, it will be run from another booted OS, not the current OS.


BTW, the OP's issue wasn't anything to do with rkhunter. It was an editor temporary file that was either left running in another window or the connection died.

---

### Post by MartyBuntu on 2021-03-28
rkhunter is a poor solution to an almost non-existent problem.

---

