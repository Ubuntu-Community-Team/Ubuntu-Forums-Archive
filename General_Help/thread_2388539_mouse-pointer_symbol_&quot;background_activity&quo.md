---
title: "mouse-pointer symbol &quot;background activity&quot;"
date: 2018-04-04
forum: General Help
---

### Post by rosika on 2018-04-04
Hi altogether,


I´ve got a question concerning my* mouse-pointer*.


From time to time my mouse-pointer changes to a symbol that represents something like an arrow melted together with a loading-circle.
I tried to find out something about it and believe that it means *"background activity"*.


So far so good. But there´s one thing I cannot really explain:


Whenever I open my file-manager pcmanfm in a "normal" way, i.e. by clicking on a desktop-icon or the respective symbol in the task-bar, the window
immediately opens - without any mose-pointer activity.


However when I start pcmanfm by clicking the key-combination "WIN-key + e" the window opens as well but with the addition of the "background-activity" symbol.
That one can be seen for about 20 seconds and then vanishes.

Another example:

I use _firejail _(sandbox) and the associated tool _firetools_. When opening _firetools_ from the menu there´s the same thing: background activity-symbol for a few seconds. But when opening via command line: no symbol whatsowever.

Just to be clear: everything works fine without any delay - even with that mouse-pointer-symbol. I just want to know why that is?


Can anyone help me?


Many thanks in advance.


Greetings.
Rosika


P.S.:
system: Linux/Lubuntu 16.04.4 LTS, 64 bit

---

### Post by rosika on 2018-04-12
[FONT=Arial]Hi again.

[/FONT]
[FONT=Arial]In the meantime I could solve the mystery. With the help of **ondoho** from [linuxquestions.org]("http://linuxquestions.org/").[/FONT]
[FONT=Arial]If anyone is interested here´s some background info:

[/FONT]
> [FONT=Arial]File: *~/.config/openbox/lxde-rc.xml*[/FONT]


[COLOR=#000000][FONT=Verdana]please have a look at that file. (warning! XML is hard to read without syntax highlighting!)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]the name might differ slightly, but you'll find it (*).[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]you will notice that most app launch entries have a section that says something like this:
[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Verdana]
      <startupnotify>
        <enabled>yes</enabled>
      </startupnotify>
[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Verdana]startup notification is a mechanism that displays the background activity pointer until it is able to recognize that the application started.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]unfortunately, [/FONT][/COLOR][I]sometimes it is not able to recognize that, so the background activity pointer just stays there until it times out.

that's what you're seeing; it does not mean that there actually is any background activity, or that the launched application has a problem. it simply means that the mechanism that displays the background activity pointer is broken.
and your system remains perfectly usable.

a small annoyance, but harmless.
[/I]


Greetings
Rosika  :)

---

