---
title: "Error on boot up: /usr/bin/do-release-upgrade"
date: 2014-09-15
forum: General Help
---

### Post by subfer1 on 2014-09-15
Every time I turn on my laptop, I get an error message telling me a software problem has been encountered; then, I don't get any details until I process the report and the report reads this:
[ATTACH=CONFIG]256463[/ATTACH]
[ATTACH=CONFIG]256464[/ATTACH]
Any thoughts? I can't really relate this to any software that I have installed, at least not as far as I can remember. The problem is not severe, as I haven't had my system crashing nor anything of the sort, but it bugs me and I want to fix whatever it is that is causing it...

Thanks!

---

### Post by slickymaster on 2014-09-15
Try to remove problematic files from **/var/lib/apt/lists/** and re-run _apt-get update_.

Open a terminal (Press Ctrl+Alt+T to launch) and run this command:```
sudo rm /var/lib/apt/lists/* -vf
```Then run```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by subfer1 on 2014-09-18
> **slickymaster said:**
> Try to remove problematic files from **/var/lib/apt/lists/** and re-run _apt-get update_.

Open a terminal (Press Ctrl+Alt+T to launch) and run this command:```
sudo rm /var/lib/apt/lists/* -vf
```Then run```
sudo apt-get update && sudo apt-get upgrade
```


When I typed in the "rm/var/lib/apt/lists/* -vf"I got a "command not found" response. :/

---

### Post by Bashing-om on 2014-09-18
subfer1; Hello;

As I pass by:
> 
When I typed in the "rm/var/lib/apt/lists/* -vf"I got a "command not found" response. :/


Try again; there should be a space between 'rm' and '/var' .
as is proper:
```

sudo rm /var/lib/apt/lists/* -vf

```

I will
[INDENT][INDENT][INDENT]pass this way again
[/INDENT][/INDENT][/INDENT]

---

### Post by slickymaster on 2014-09-19
@subfer1
Like Bashing-om correctly stated you missed the space between the command **rm** and the path to which the command relates to.

@Bashing-om
Thanks for having my back covered.

---

### Post by Bashing-om on 2014-09-19
> **slickymaster said:**
> @subfer1
Like Bashing-om correctly stated you missed the space between the command **rm** and the path to which the command relates to.

@Bashing-om
Thanks for having my back covered.

:) consider only a small amount of pay back ! How many times have you covered mine ?

[INDENT][INDENT]'buntu
[INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by subfer1 on 2014-09-22
Guys, thank you for pointing that error out. I ran the codes you gave me and they seemed to have worked. Then I started getting a notification telling me one of my packages was not working, (which before my system could not ID). I just went into the terminal and checked for errors and upgraded the packages and it's now working fine. 
Thank you all very much :)

---

### Post by slickymaster on 2014-09-22
You're welcome. Happy *buntuing.

---

