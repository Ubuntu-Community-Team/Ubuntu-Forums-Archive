---
title: "Problem with opening folders as root and installing nautilus-admin"
date: 2019-06-27
forum: General Help
---

### Post by antarmanu on 2019-06-27
I have recently installed Ubuntu 18.04 on a laptop and I need to have the ability to open a folder as administrator. In Linux Mint it's quite easy because you have that option in the menu when you right-click a folder. But here in Ubuntu, there is no such option.

Following instructions outlined in this tutorial:

[https://www.groovypost.com/howto/open-files-folders-as-administrator-in-nautilus-ubuntu/](https://www.groovypost.com/howto/open-files-folders-as-administrator-in-nautilus-ubuntu/)

I tried to install nautilus-admin by typing

```

sudo apt-get install nautilus-admin


```

But I always get the error message that the package cannot be located.

"E: Unable to locate package nautilus-admin"


I tried to type "sudo apt-get update" but the error persists, and I can't install that package. 

Any ideas what I could do?

---

### Post by antarmanu on 2019-06-27
To answer my own question, the problem was that the default server for  software updates was set up for my local country, and that server  doesn't seem to be working. When I switched to USA it started working  and I can install nautilus-admin and any other program.

---

