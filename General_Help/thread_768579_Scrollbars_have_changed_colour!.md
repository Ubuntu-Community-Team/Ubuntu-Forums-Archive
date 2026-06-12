---
title: "Scrollbars have changed colour!"
date: 2008-04-26
forum: General Help
---

### Post by melat0nin on 2008-04-26
Hi all

My update manager updated the gtk-murrine (sp?) package and now all my scollbars are orange, whereas before they were a nice muted grey just like the up and down arrows at the top and bottom of them.  It's really distracting and I don't like it.

How can I change it back?

---

### Post by dbbolton on 2008-04-26
After you pick your Controls, click on the Color tab. At the bottom, click the button that says "revert".

---

### Post by melat0nin on 2008-04-27
> **dbbolton said:**
> After you pick your Controls, click on the Color tab. At the bottom, click the button that says "revert".

The revert button is not enabled - so I changed another colour and then clicked it, but that did not work.

I should have clarified that it's not the whole scrollbar that is orange, just the bit that moves when scrolled (the bar within the scrollbar).

---

### Post by dbbolton on 2008-04-27
> **melat0nin said:**
> The revert button is not enabled - so I changed another colour and then clicked it, but that did not work.

I should have clarified that it's not the whole scrollbar that is orange, just the bit that moves when scrolled (the bar within the scrollbar).
Could you post a screenshot?

---

### Post by Ub1476 on 2008-04-27
What theme are you using?

---

### Post by melat0nin on 2008-04-27
> **dbbolton said:**
> Could you post a screenshot?

Sure thing:

[IMG]http://i26.tinypic.com/2lscy8l.png[/IMG]


I"m sure it's the Human-Murrine theme which has seemingly been updated with orange bars.  I just don't like them as much as the grey bars which are less obtrusive

---

### Post by melat0nin on 2008-04-27
> **Ub1476 said:**
> What theme are you using?

I'm using Human-Murrine, which came with Hardy.  It appeared to be updated sometime yesterday though, which turned the scrollbar-bars(!) orange from the grey that they were.

---

### Post by dbbolton on 2008-04-27
> **melat0nin said:**
> I'm using Human-Murrine, which came with Hardy.  It appeared to be updated sometime yesterday though, which turned the scrollbar-bars(!) orange from the grey that they were.
So it's only this one theme with the problem? If you just want to change the scrollbar color of this particular theme, I can tell you how to do that. 

Since this theme came with the installation, I would guess that there is gtkrc file located at /usr/share/themes/Human-Murrine/gtk-2.0/ (themes that you install will be put in /home/yourusername/.themes/nameoftheme). You will need to find this file and edit it as root, like this:

```

gksudo gedit /usr/share/themes/Human-Murrine/gtk-2.0/gtkrc

```

Look for a section like this:

```

  engine "murrine" 
  {
    menuitemstyle         = 2
    scrollbar_color         = "#686966"
    scrollbarstyle         = 3
    contrast             = 1.0
    menustyle              = 0
    glazestyle              = 0
    menubarstyle          = 0
    menubaritemstyle     = 0
    menuitemstyle          = 0
    listviewheaderstyle = 0
    listviewstyle         = 1
    gradients            = FALSE
    roundness             = 0
    animation             = TRUE
    hilight_ratio         = 0.909090
  }

```

There you can change scrollbar_color to whatever you want. Let me know if this helps.

---

### Post by melat0nin on 2008-04-28
> **dbbolton said:**
> So it's only this one theme with the problem? If you just want to change the scrollbar color of this particular theme, I can tell you how to do that. 

Since this theme came with the installation, I would guess that there is gtkrc file located at /usr/share/themes/Human-Murrine/gtk-2.0/ (themes that you install will be put in /home/yourusername/.themes/nameoftheme). You will need to find this file and edit it as root, like this:

```

gksudo gedit /usr/share/themes/Human-Murrine/gtk-2.0/gtkrc

```

Look for a section like this:

```

  engine "murrine" 
  {
    menuitemstyle         = 2
    scrollbar_color         = "#686966"
    scrollbarstyle         = 3
    contrast             = 1.0
    menustyle              = 0
    glazestyle              = 0
    menubarstyle          = 0
    menubaritemstyle     = 0
    menuitemstyle          = 0
    listviewheaderstyle = 0
    listviewstyle         = 1
    gradients            = FALSE
    roundness             = 0
    animation             = TRUE
    hilight_ratio         = 0.909090
  }

```

There you can change scrollbar_color to whatever you want. Let me know if this helps.

That worked! I just changed it to the same colour as the @bgcolor variable set at the top of the file.

I had no idea themes were so easily changed (should have expected it, this being Linux, after all) -- it's not a million miles from CSS.  Might give it a try myself sometime!

Thanks for the help, I really appreciate it :)

---

### Post by dbbolton on 2008-04-28
No problem :)

---

### Post by msrinath80 on 2011-05-07
I know this is an old thread, but nevertheless, thanks for that tip dbbolton. I found it just as useful!

---

