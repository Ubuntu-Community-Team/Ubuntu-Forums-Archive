---
title: "X11 keyboard layout vs vc keyboard layout"
date: 2015-01-07
forum: General Help
---

### Post by yoreei.grigorov on 2015-01-07
Hi!
I am running Kubuntu 14.04 and I am a Neo keyboard layout user. Setting it in the GUI was easy but it didn't last when I entered tty. I was sent back to qwerty. Trying to solve the problem with localectl:
```
localectl -list-keymaps
```
returned that it couldn't find any console keymaps (and indeed /usr/share/keymaps was missing). So I installed the console-data package to fix this. heading to the newly created /usr/share/keymaps/i386 I was left disappointed because there resided only a few layouts (of which Neo wasn't present)

What struck me by this whole process was the division between the X keymapping and the virtual console keymapping. Why should such a difference exist? We have different files describing layouts, different commands to manage them... Can't X11 just use the virtual console configuration or vice versa?

Another peculiar thing I observed was the fact that there was so much information on Google about X keymapping but at the same time no one seemed interested in changing the layout of the console. Why is that? Even searching the Neo website [http://neo-layout.org/](http://neo-layout.org/) I could find information only regarding X11.

I know my question doesn't address a specific problem I have but rather my confusion regarding how things are done in the linux keymapping department so I am not sure if General HELP is the right place. Please, correct me on this if you know where it will suit better.

In short: What happened to the virtual console keymapping and how is keymapping relevant to X's job 
PP: I was thinking of making a virtual console version of the Neo layout but given the lack of interest in this area (by which I'm astounded) I am worrying it will be close to useless to other people. What do you thing on the subject? If it were useful only to me, I'd rather use qwerty in console.
Thank you in advance!

---

### Post by DuckHook on 2015-01-07
Disclosure: I don't really know anything about Neo. Yours is the first I've even ever heard of it. But if I might indulge in some general observations:

I'm afraid, that we console users don't get much love these days. If anything, Linux would provide the most support, but even here, it's slim pickins'.

X uses its own keymappings and does not rely on the console because it does not want to be constrained by console limitations. This creates the perverse feedback cycle that you are now struggling with: new development tends to be directed only at X and the console gets orphaned even further. I have Chinese-speaking friends who suffer from similar console limitations, and none of them have found a purely console solution to their issue.

You are always not only welcome, but encouraged to add to Linux-space by writing a Neo console keymap. I think you would get an enthusiastic reception from the maintainers of the *console-data* package. But in the end, I doubt that a Neo console would find much traction among the user base. The console crowd seems to be thinning out these days and even hard-core development work is done inside a GUI. Finally, the vast majority of any residual console jockeys are probably qwerty touch-typists who would never switch to anything else.

Curiosity question: what do you use your console for?

---

### Post by yoreei.grigorov on 2015-01-08
Thank you for the answer! What you said was what I feared the most. I really hoped that someone could prove my speculations wrong. Still, I feel much better about this subject now that I know how the situation with the console really is. 
With this in mund, I wouldn't direct my enthusiasm in making a console keymapping now. I'll just keep it as an idea for when I am bored :)

And now for the curiosity thing: I am still a relative newbie in the console world so what I do there the most can be described mainly by "learning"
My reason to have such an avid interest in the console is the fact that this way I can observe how the system really works on a lower-than-GUI level.
Another thing as the efficiency with which I can get jobs done or get them automated
A third reason is the availability of all kinds of tools with CLI probably because GUI demands more work even nowadays.
Last but not least is the level of distribution agnostcity. Of course there are differences but not as much as there can be in the GUI. I don't want to be dependant on the availability of my favourite DE
Although your answer fully satisfying, I'll wait with the solved tag because someone might want to opt in too

---

