---
title: "Netbeans GUI Builder ugly with dark GTK+ theme"
date: 2013-02-22
forum: General Help
---

### Post by JaySeeJC on 2013-02-22
Not sure where to post this.
Just wondering if anyone around here knows how to beat netbeans' GUI builder into not looking like crap with a dark GTK+ theme. Currently, this is what i'm seeing:
[img]https://dl.dropbox.com/u/51261980/Snapshots/Screenshot%20from%202013-02-22%2009%3A58%3A58.png[/img]

---

### Post by slickymaster on 2013-02-22
The default look and feel of NetBeans IDE is set automatically according to the operating system. This make the NetBeans appear as a Windows application with Windows look and feel while running on windows and so forth in other operating systems.

In order to change it, you have to edit the **netbeans.conf** file passing it the exact fully qualified name of the look and feel class you want.

Suppose you want to use metal look and feel, which fully qualified name is javax.swing.plaf.metal.MetalLookAndFeel.
What you'll do is to open **netbeans.conf** file in a text editor and change the **netbeans_default_options** adding one additional switch to it. In this case you will add the look and feel option like:
```
--laf javax.swing.plaf.metal.MetalLookAndFeel
```
Please note that the value you're adding has to be place just before the last double quotes.

Now when you start NetBeans again the look and feel will be seen as Metal.

---

### Post by slickymaster on 2013-02-22
There is of course a lot more Look and Feel packages available, besides the one I mentioned in my previous post.

I'll leave you the fully qualified name of just a few:
```
javax.swing.plaf.metal.MetalLookAndFeel
javax.swing.plaf.nimbus.NimbusLookAndFeel
com.sun.java.swing.plaf.motif.MotifLookAndFeel
com.sun.java.swing.plaf.gtk.GTKLookAndFeel
```

---

### Post by JaySeeJC on 2013-02-22
I already have that option on to set it to my GTK+ theme. The problem is the GUI builder is picking up half my GTK theme while with the rest being filled in with those ugly light colors. the rest of netbeans looks fine. Notice how the menu in the GUI builder has light text on a ligh background. Is there any way to have all of the GUI builder comply to one theme or the other, preferably without using another theme for netbeans?

---

### Post by slickymaster on 2013-02-22
If you want the same for your NetBeans Platform application add to project (suite) **project.properties** file this line:
```
run.args.extra=—laf Gtk
```

---

### Post by JaySeeJC on 2013-02-22
That works for when the app actually launches, but the GUI builder is still using the half gtk theme.

---

### Post by slickymaster on 2013-02-22
Well, that's bizarre, to say the least. How are you designing your frame? What I mean is what Layout Manager are you using for the design of your frame/GUI application?

---

