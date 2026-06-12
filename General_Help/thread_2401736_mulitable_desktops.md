---
title: "mulitable desktops"
date: 2018-09-21
forum: General Help
---

### Post by oneleded on 2018-09-21
i'm running 18.04.1LTS.. though this isnt a major problem, i dont like the fact since 14.04 LTS, when scrolling the center wheel, it switches between desktops. i know this is important to some, but i do good just to have 1 desktop. how can i stop this for me? i changed to lubuntu from xp because i didnt like the direction windows, was going. doubt i ever learned xp all that well. but when vista came around, i didnt want to bother. i know this is too much information,, sometimes i cant help myself. i do like linux, its more user friendly.  //Ed

---

### Post by Dennis N on 2018-09-21
You can change to one desktop: Right click on the desktop switcher, and open "Desktop Pager" settings. Change number of desktops to 1.
(My mouse wheel in Lubuntu 18.04 doesn't switch the desktops (I have to click on another desktop to switch to it), so there must be another setting that was made.)

---

### Post by poorguy on 2018-09-21
Hey oneleded,


Lower left hand corner of panel / taskbar ***blue box*** circle icon in center ***left click to open***.

Under ***Preferences*** look for ***Openbox Configuration Manager ***and ***left click it to open***.

Look for ***Desktops*** and ***left click the minus sign*** to remove the number of desktops from ***2 ***to*** 1***.

***Close menu*** and you should be good to go with only 1 desktop.


[IMG]https://3.bp.blogspot.com/-0SDn8IXU_hs/V8FEw92MHJI/AAAAAAAAEy0/3HKC7Q1ai4Q99dDdJwtU2f51XsZeOffkgCLcB/s1600/software-updates-lubuntu-16.04.png[/IMG]

---

### Post by Dennis N on 2018-09-21
> when scrolling the center wheel, it switches between desktops...

Here is how this is fixed:

I checked my **~/.config/openbox/lubuntu-rc.xml** file which contains _lots_ of Lubuntu settings.

Comment out lines 773 to 802 and the mouse wheel won't switch workspaces when over the desktop. "Comment out" means surround a code section to be ignored with a pair of symbols **<!--** and **-->** as shown below (in red):

```
    <context name="Desktop">
**[COLOR="#FF0000"]<!--[/COLOR]**      <mousebind button="Up" action="Click">
        <action name="GoToDesktop">
          <to>previous</to>
        </action>
      </mousebind>
      <mousebind button="Down" action="Click">
        <action name="GoToDesktop">
          <to>next</to>
        </action>
      </mousebind>
      <mousebind button="A-Up" action="Click">
        <action name="GoToDesktop">
          <to>previous</to>
        </action>
      </mousebind>
      <mousebind button="A-Down" action="Click">
        <action name="GoToDesktop">
          <to>next</to>
        </action>
      </mousebind>
      <mousebind button="C-A-Up" action="Click">
        <action name="GoToDesktop">
          <to>previous</to>
        </action>
      </mousebind>
      <mousebind button="C-A-Down" action="Click">
        <action name="GoToDesktop">
          <to>next</to>
        </action>
      </mousebind> **[COLOR="#FF0000"]-->[/COLOR]**
```

You can do the same.

---

### Post by oneleded on 2018-10-06
thanks for the info. i changed to 1 desktop, for now..

---

