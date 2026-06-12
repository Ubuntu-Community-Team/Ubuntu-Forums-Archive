---
title: "Official Repository Applications not found in Ubuntu Software"
date: 2017-02-25
forum: General Help
---

### Post by DB4711 on 2017-02-25
Hello,

I want to install xdotool. As I can read here [https://wiki.ubuntuusers.de/xdotool/](https://wiki.ubuntuusers.de/xdotool/) it's an official Application from Ubuntu repository. I can klick on the Page to install it. But I can't find it when I search in Ubuntu Software. Should I? If yes, did I miss something to configure?

---

### Post by mikewhatever on 2017-02-25
It's hard to tell what is wrong from the provided info. Open a terminal window and run 
```
sudo apt-get install xdotool
```

and post the output.

---

### Post by DB4711 on 2017-02-25
Hello mikewhatever,

thanks for your help. I just ask myself why I can't find this tool in my Ubuntu Software Center as it is available through official repository. I want to understand why?

---

### Post by howefield on 2017-02-25
Not a tool I'm familiar with but isn't it a command line tool, used and configured from the terminal ?

```
man xdotool
```

There are many tools not available from the Software Centre / Ubuntu Software including most commandline tools, but installable as suggested by mikewhatever.

---

### Post by DB4711 on 2017-02-25
Hello howefield. I use it to autocomplete my keeppass credentials in firefox. But it is only an example. I just ask myself why I can't find this tool in my Ubuntu Software Center as it is available through official repository. I want to understand why?

---

### Post by vasa1 on 2017-02-25
> **DB4711 said:**
> Hello,

I want to install xdotool. As I can read here [https://wiki.ubuntuusers.de/xdotool/](https://wiki.ubuntuusers.de/xdotool/) it's an official Application from Ubuntu repository. I can klick on the Page to install it. But I can't find it when I search in Ubuntu Software. Should I? If yes, did I miss something to configure?

> **DB4711 said:**
> Hello howefield. I use it to autocomplete my keeppass credentials in firefox. But it is only an example. I just ask myself why I can't find this tool in my Ubuntu Software Center as it is available through official repository. I want to understand why?

So do you have it installed or not? If you have it installed, why is Ubuntu Software Center (USC) involved?

USC not seeing it is another matter. I've seen a lot of complaints about USC. Try Synaptic Package Manager instead.

---

### Post by howefield on 2017-02-25
> **DB4711 said:**
> Hello howefield. I use it to autocomplete my keeppass credentials in firefox. But it is only an example. I just ask myself why I can't find this tool in my Ubuntu Software Center as it is available through official repository. I want to understand why?

Which Ubuntu release are you using ?

In 16.04 the Ubuntu Software Centre became Ubuntu Software, a new software centre. If 16.04 is the release that you are using then it is probably incomplete appstream data which is still a work in progress, a workaround is to install the old Software Centre but probably not a solution for you specifically as you only want to understand why the package is not there :)

Other alternatives are to install Synaptic package manager or, as is my preference, use the command line to search for and install packages.

---

### Post by speartip on 2017-02-25
Try installing Synaptic, & search for your software that way. IMO, it's a far more reliable method than using the Software Centre.

---

### Post by Autodave on 2017-02-25
*xdotool *is found in *Synaptic* in 16.04.

---

