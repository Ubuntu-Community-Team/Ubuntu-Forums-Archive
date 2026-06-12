---
title: "Nautilus help"
date: 2007-02-15
forum: General Help
---

### Post by igknighted on 2007-02-15
Ok, as a long time KDE user, I am giving gnome a go... but I need a little help with nautilus before I lose my mind.

1) How can I get nautilus to stop opening each folder in a new window?  <-- this is the showstopper, I can't stand this

2) Is there a way to get a bar there so I can type the path to the folder I want?

3) If nautilus can't do what I want, what other GTK filebrowsers might be able to?

---

### Post by erkki70 on 2007-02-15
Hi,

1- Try this:

```
gconftool-2 --type bool --set /apps/nautilus/preferences/always_use_browser true
```
or
in gconf-editor, set **/apps/nautilus/preferences/always_use_browser** to true.

2- And this:

```
gconftool-2 --type bool --set /apps/nautilus/preferences/always_use_location_entry true
```
or
in gconf-editor, set **/apps/nautilus/preferences/always_use_location_entry** to true.

Enjoy :-)

Cheers

---

### Post by SuSUntu on 2007-02-15
**As an alternative to Erkki70's recommendations**

> **igknighted said:**
> 
1) How can I get nautilus to stop opening each folder in a new window?  <-- this is the showstopper, I can't stand this


Edit -> Preferences -> Behavior: Check "Always Open In Browser Windows"

Note: Although the default behavior of Gnome Nautilus is [spatial mode]("http://www.gnome.org/learn/users-guide/2.14/nautilus-spatial-mode.html") (open a new window each time), I could have sworn that out-of-the-box-Ubuntu overrode that default and selected "Always Open In Browser Windows" (which is known as "[browser mode]("http://www.gnome.org/learn/users-guide/2.14/nautilus-browser-mode.html")"). Did you change it without realizing it? Or did you perhaps install a different version of Gnome?  

> **igknighted said:**
> 
2) Is there a way to get a bar there so I can type the path to the folder I want?


From a browser-mode Nautilus window (per the set-up described in Item #1), select (if not already selected):

View -> Location Bar

Once you have selected that view option, you will see an icon to the left of the location bar that looks like a piece of paper with a pencil on it. That icon toggles between button-based navigation and text-based navigation in the bar. If you see buttons representing the file path, click the paper-and-pencil icon and it will change the display to a traditional text-box location bar. 

> **igknighted said:**
> 
3) If nautilus can't do what I want, what other GTK filebrowsers might be able to?


I supplement Nautilus with [EmelFM2]("http://www.emelfm2.net/"), a highly configurable and option-rich traditional two-pane browser.

By the way, launching Nautilus with:

nautilus **--browser** [path]

will override the global spatial mode preference setting. There is no such override parameter for launching spatial-mode windows if the "Always Open In Browser Windows" preference is selected. So, I prefer to leave spatial mode on globally (e.g., de-select "Always Open In Browser Windows" option), and then I specifically set my Nautilus launchers to use browser mode (--browser) when desired. That way you can have launchers that open browser-mode windows and spatial-mode windows. Despite your apparent disdain for spatial mode (I wouldn't care for it at all either if I didn't have the option to choose when to use it), spatial mode does have its benefits.

**
On a side note, I have (at least) two issues with Nautilus myself:

1. When launching a root Nautilus instance with gksudo, the "busy" indicator (mouse pointer animation) stays running for about 15-20 seconds, even on a powerful PC. While the "busy" indicator is spinning, the mouse can still be used and Nautilus still responds to clicks from this animated pointer. So, basically, it's just annoying waiting for the "busy" indicator to return to the normal mouse pointer. This behavior does not occur when launching normal Nautilus windows (non-root). 

2. After upgrading from Dapper to Edgy, the Nautilus File Properties Permissions Tab has been dumbed way-down and doesn't allow for fine-grained control. There are no Set UID, Set GID, or sticky bit options, and worst of all, the only way to set a file as "executable" is to set it executable for owner, group and OTHER (it's all or nothing). I know how to set permissions from the command line or in EmelFM2, but I simply cannot see the logic of making such changes to the GUI. If they are going to dumb the interface down that much, they might as well remove the permissions tab entirely.

---

### Post by fragos on 2007-02-15
I'm a Gnome convert from KDE my self.  I did the same things you want to as outlined by others but also found a very powerful feature in Nautilus Scripts.  My two favorites are "Open as Administrator" which gives you root access according to what ever application is normally used.  For example Gedit.  If you open a folder with this feature all Nautilus initiated programs will come up as root.  The second is "Terminal Here" which opens the terminal window set to that directory.  No end of scripts can be created.  You can even write them in bash.

---

### Post by vector_prime on 2007-02-17
> **SuSUntu said:**
> 2. After upgrading from Dapper to Edgy, the Nautilus File Properties Permissions Tab has been dumbed way-down and doesn't allow for fine-grained control. There are no Set UID, Set GID, or sticky bit options, and worst of all, the only way to set a file as "executable" is to set it executable for owner, group and OTHER (it's all or nothing). I know how to set permissions from the command line or in EmelFM2, but I simply cannot see the logic of making such changes to the GUI. If they are going to dumb the interface down that much, they might as well remove the permissions tab entirely.

There's a gconf setting for this.  Go into gconf-editor and try setting /apps/nautilus/prefrences/show_advanced_permissions to true.

---

### Post by SuSUntu on 2007-02-17
> **vector_prime said:**
> There's a gconf setting for this.  Go into gconf-editor and try setting /apps/nautilus/prefrences/show_advanced_permissions to true.

Perfect.

Thank you very much for that information. :)

---

### Post by CocoAUS on 2007-02-17
What version of Ubuntu are you using?  My default Edgy install doesn't use the stupid open-a-new-window-for-every-folder behavior.

Since I've configured Nautilus correctly, the only complaint I have about Gnome is that the stupid wxwidgets behavior makes sliders (in Totem, for instance) jump by intervals, rather than jumping to where you click.  Oh, and the stupid file chooser in save dialogs and such is horrible.  Absolutely horrible.

Other than that, I love Gnome better than KDE in every way.

---

### Post by NoobieDoobieDo on 2007-12-03
OMFG thank you - I can't stand how Nautilus opens a new window everytime.

Most. Retarded. Thing. Ever.

Seriously, don't ever program Gnome to do this again.

---

### Post by fragos on 2007-12-03
> **NoobieDoobieDo said:**
> OMFG thank you - I can't stand how Nautilus opens a new window everytime.

Most. Retarded. Thing. Ever.

Seriously, don't ever program Gnome to do this again.

You should check your facts before making statements.  In this case your assertion is wrong and taken out of context of how things work.  If you open a folder on the desktop or thru Places you get a new window.  If you open a folder within a Nautilus window it opens in that window.  Both ways have their place.  Two windows certainly works well when draging files from one place to another.  Having both options is hardly retarded.

---

