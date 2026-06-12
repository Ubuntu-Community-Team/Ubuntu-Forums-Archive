---
title: "Printer Menu Missing in Edgy"
date: 2006-11-29
forum: General Help
---

### Post by tomcat1965 on 2006-11-29
Is it just me or has anyone else not got a printer menu under System>Administration?......Would be handy to have as I want to share my printer with my laptop and I haven't got an entry in the system menu to go and configure it,I checked in the menu layout box and there is no option to add it.
Any ideas anyone?
I was very pleased to find I can print directly onto CD,I really didn't think that function would ever work( Epson stylus photo R300)
Shows how good Ubuntu 6.10 is when my only problem is a missing menu entry!!!:)

---

### Post by ciscosurfer on 2006-11-29
The Printing panel is located under System > Administration.

You can choose which printer to use there.   Also, when you choose to print a doc, you can select which printer you want to use.

You can use **gnome-cups-manager** or **gnome-cups-add** in a terminal.

---

### Post by tomcat1965 on 2006-11-29
:( Not for me it isn't unfortunately..I have under system>Administration network tools and then Services....nothing beginning with P.
Can't work out why not,like I said not even in the preferences menu to add for some reason.
My printer is working fine just want to be able to set it up to share with my Laptop.

---

### Post by ciscosurfer on 2006-11-30
> **tomcat1965 said:**
> :( Not for me it isn't unfortunately..I have under system>Administration network tools and then Services....nothing beginning with P.
Can't work out why not,like I said not even in the preferences menu to add for some reason.
My printer is working fine just want to be able to set it up to share with my Laptop.How did you get your printer setup if there's no Printing admin panel?  Did you use the command-line?

---

### Post by tomcat1965 on 2006-11-30
Yep,used the command line and only just yesterday noticed it was missing from the menu..weird.
Not too bothered as have edited my samba.conf file and am sharing the printer just can't work out why its not an option to add to the menu,I thought I might have unchecked the box but no,I haven't got a printer item to add.
Would like a way to get it added though!

---

### Post by ciscosurfer on 2006-11-30
> **tomcat1965 said:**
> Yep,used the command line and only just yesterday noticed it was missing from the menu..weird.
Not too bothered as have edited my samba.conf file and am sharing the printer just can't work out why its not an option to add to the menu,I thought I might have unchecked the box but no,I haven't got a printer item to add.
Would like a way to get it added though!This should be relatively easy to fix.  [LIST=1]
[*]Go to System > Preferences > Menu Layout
[*]Administration is a submenu of System.  Go ahead an click Adminisration.
[*]If Printing is unchecked, go ahead an recheck it and it should appear in your menu again.
[*]If Printing (for whatever reason) doesn't not exist, then create it.[/LIST][LIST]
[*]Click New Item
[*]Name: Printing
[*]Comment: Configure your printers
[*]Command: gnome-cups-manager
[*]For the icon, you can use whatever you like, but the default GNOME CUPS icon is located under /usr/share/applications and is called Printing Notification Icon
[*]Click OK[/LIST]Your Printing Menu should now be intact and ready to go.

Post back if you have any trouble. :-D

---

### Post by tomcat1965 on 2006-12-02
How weird,didn't think to check icons,but I've got no printer icon,all the others though... and if I enter gnome-cups-manager I get the error message "Failed to execute child process"gnome-cups-manager"(No such file or directory)":???:........ 
just a glitch though,I re-installed cups-manager gui from synaptic and got menu item back,thanks for your help,much appreciated,should have thought of re-installing from synaptic earlier:D

---

### Post by ciscosurfer on 2006-12-03
> **tomcat1965 said:**
> [...]just a glitch though,I re-installed cups-manager gui from synaptic and got menu item back,thanks for your help,much appreciated,should have thought of re-installing from synaptic earlier:DAbsolutely!  Not a problem, and glad I could help. :KS

---

