---
title: "desktop effects could not be enabled"
date: 2008-06-02
forum: General Help
---

### Post by F35Blackbird on 2008-06-02
Hello,

I just installed 8.04LTS from scratch on my Dell 600M laptop. When I had 7.10 on the same machine, I was able to set "Visual Effect" to "Extra". Now when I do that, I get an error "Desktop effects could not be enabled". I have no idea what to do!

When I type the command "compiz" on my terminal, I get this output.

Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity 

Can anyone help!!

Thanks!

---

### Post by Rocket2DMn on 2008-06-02
You are in luck, I have the same model laptop.  Have a look here: [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by Forlong on 2008-06-02
> **F35Blackbird said:**
> When I had 7.10 on the same machine, I was able to set "Visual Effect" to "Extra" 
[...]
Found laptop using ati driver.
In this case all you need to do is skip the blacklist:
```
mkdir -p $HOME/.config/compiz && echo SKIP_CHECKS=yes >> $HOME/.config/compiz/compiz-manager
```

---

### Post by Rocket2DMn on 2008-06-02
> **Forlong said:**
> In this case all you need to do is skip the blacklist:
```
mkdir -p $HOME/.config/compiz && echo SKIP_CHECKS=yes >> $HOME/.config/compiz/compiz-manager
```

There's an echo in here! :)

That's what I have in the link I posted above.  You can find other known bugs and workarounds in Hardy here - [http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851)

---

### Post by Forlong on 2008-06-02
Sorry, I just saw "HowTo" and didn't want F35Blackbird confused that he/she needs to install anything to make it work.

---

### Post by F35Blackbird on 2008-06-04
Thanks a lot to both of you!!!

in a nutshell, I used the following 2 commands and everything worked perfectly fine after that.

mkdir -p $HOME/.config/compiz && echo SKIP_CHECKS=yes >> $HOME/.config/compiz/compiz-manager

sudo apt-get install compizconfig-settings-manager

---

