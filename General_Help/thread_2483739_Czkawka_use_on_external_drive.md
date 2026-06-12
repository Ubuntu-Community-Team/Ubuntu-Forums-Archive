---
title: "Czkawka use on external drive?"
date: 2023-02-07
forum: General Help
---

### Post by boreal4 on 2023-02-07
Hey all!

im trying to cleanup an external hard drive with Czkawka but it doesnt seem to allow me to use it with an external drive. Does anyone know if this is possible? or how to do it?
Or does anyone know of a different app that would do this?
thanks in advance!

---

### Post by teabeamet on 2023-10-30
WHY Software developers are doing this kind of things, rendering software coplete useless. after hours of research, finally Finding software that can do what is needed, only one that was able to install normally, and then, by some freak reason it is hard coded so it can not be run in root and also can not scan actual file arcives on external harddrives. 

All other less capabale softwares can do it and now, this one, advanced one, can not ? 

Does not make sense. 


[https://qarmin.github.io/czkawka/instructions/Instruction.html](https://qarmin.github.io/czkawka/instructions/Instruction.html) 

and what is that, in here, told about "[COLOR=#24292E][FONT=-apple-system]external drivers" 

I mean, all honor to a developer, (rsflint was not able to work) but WHY user is forced to security that we do not need, whit out options to disable it.
 __

[/FONT][/COLOR]############### MESSAGES(2) ###############
Properly saved to file 2 cache entries.
Properly saved to file 2 cache entries.
############### WARNINGS(12) ###############
Cannot open dir &#8296;/media/marijuana/16TB&#8297;, reason &#8296;Permission denied (os error 13)&#8297;
Cannot open dir &#8296;/home/marijuana/.local&#8297;, reason &#8296;Permission denied (os error 13)&#8297;
Cannot open dir &#8296;/home/marijuana/.pinot&#8297;, reason &#8296;Permission denied (os error 13)&#8297;
Cannot open dir &#8296;/home/marijuana/.kde&#8297;, reason &#8296;Permission denied (os error 13)&#8297;
Cannot open dir &#8296;/home/marijuana/.cache&#8297;, reason &#8296;Permission denied (os error 13)&#8297;
Cannot open dir &#8296;/home/marijuana/.cinnamon&#8297;, reason &#8296;Permission denied (os error 13)&#8297;
Cannot open dir &#8296;/home/marijuana/.icons&#8297;, reason &#8296;Permission denied (os error 13)&#8297;
Cannot open dir &#8296;/home/marijuana/.pki&#8297;, reason &#8296;Permission denied (os error 13)&#8297;
Cannot open dir &#8296;/home/marijuana/.config&#8297;, reason &#8296;Permission denied (os error 13)&#8297;
Cannot open dir &#8296;/home/marijuana/.thumbnails&#8297;, reason &#8296;Permission denied (os error 13)&#8297;
Cannot open dir &#8296;/home/marijuana/Allalaadimised/czkawa&#8297;, reason &#8296;Permission denied (os error 13)&#8297;
Cannot open dir &#8296;/home/marijuana/Allalaadimised/rmlint&#8297;, reason &#8296;Permission denied (os error 13)&#8297; 

___

We need solution, please, 
ignoring any kind of safty worry that has caused it, manual settings has some options on it ?

---

### Post by Holger_Gehrke on 2023-10-30
Are you perhaps using the snap of "Czkawka" ? In that case you need to give it permission to access removable media. So you can either enter
```

sudo snap connect czkawka:removable-media

```
in a terminal or remove the snap and use the AppImage. Snaps are normally forbidden from opening files outside the home directory of the user (except for snaps running in either developer or classic mode). They are also not allowed to access hidden files and directories directly in the users home (normally not a problem; those are mostly configuration files for non-snap applications and there's no good reason one application should access another programs config).

So it's actually not a problem of the program but of the package-format. snap is not a good fit for this kind of tool.

Holger

---

### Post by rich-weideman on 2024-01-05
Thanks @[COLOR=#000000]Holger_Gehrke

Your tip sorted it out for me.[/COLOR]

---

### Post by saskiac on 2024-12-04
Hi Holger, i have czkawka installes via software manager on mint and now trying to acces external drive. the command you give sudo snap connect czkawka:removable-mediagives me back: 
sudo: connect: command not found
Can you help me please? I have more issues using mint and accessing external harddrive. 
Thank you!

---

### Post by coffeecat on 2024-12-04
Hello saskiac, this is an old thread, and this forum is shortly to close down with support moving to Ubuntu Discourse. A few points.

[list=1][*]Linux Mint does not come with snaps, so issuing snap commands will fail.
[*]Please do not post to Ubuntu Discourse. Although based on Ubuntu, Linux Mint is not Ubuntu, and I believe that Ubuntu Discourse will close threads about Mint as being off-topic.
[*]The best place for Linux Mint questions is on their own forum here: [https://forums.linuxmint.com/](https://forums.linuxmint.com/)
[*]Hijacking old threads is not looked on favourably on most forums, and is best avoided.[/list]

Old thread closed.

---

