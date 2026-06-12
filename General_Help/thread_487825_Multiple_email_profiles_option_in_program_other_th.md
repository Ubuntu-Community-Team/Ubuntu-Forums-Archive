---
title: "Multiple email profiles option in program other than Thunderbird?"
date: 2007-06-29
forum: General Help
---

### Post by MCSE_Crossover on 2007-06-29
Ok. My wife and I share the same computer - but we use the same logon. We use Thunderbird for our email program because it has the "Profile Manager" and lets us set up two totally seperate email programs and then we are prompted for which one we want to open when we start Thunderbird.

Well, Thunderbird (and Firefox) for some reason to not offer the ability to preview an image when going through the file browser. So, in Thunderbird, if we are sending an email of our kids and we want to attacha picture, when we click "attach," the only thing that we can see is the text description of the image with no actual thumnail view or image preview.

This seems to be something specific to Mozilla applications. Is there another email program that offers the profile manager ability? I couldn't find it in Evolution or Kmail. Those programs both offer the ability to view thumbnails though.

What is weird is that MS Outlook offers this capability and Evolution is supposed to be an Outlook replacement - yet I was unable to find this feature within Evolution. Hopefully someone can shed some light on this for me.

---

### Post by Brucevdk on 2007-06-29
> **MCSE_Crossover said:**
> This seems to be something specific to Mozilla applications. Is there another email program that offers the profile manager ability? I couldn't find it in Evolution or Kmail. Those programs both offer the ability to view thumbnails though.

If you're talking about the file chooser, then no that's not really specific to Mozilla applications, it's the good old GtkFileChooserDialog. From what I hear/read it hasn't changed all that much since < 2004.

If you were talking about the profile manager functionality, well that is something Mozilla specific though I took a quick look at KMail and it does seem to have something called "identities". There's also a tiny chance that it's possible to use KDE/QT dialogs in Mozilla Thunderbird, though I Googled a few seconds and all I could find was references to the *ui.allow_platform_file_picker* variable in *about:config*. I wouldn't get your hopes up.

> **MCSE_Crossover said:**
> Well, Thunderbird (and Firefox) for some reason to not offer the ability to preview an image when going through the file browser. So, in Thunderbird, if we are sending an email of our kids and we want to attacha picture, when we click "attach," the only thing that we can see is the text description of the image with no actual thumnail view or image preview.

What I personally do is avoid the file chooser dialog and just use Nautilus + drag and drop to attach any attachments, that might work for you guys.

I really have to ask does anybody here know if the GNOME/GTK team is planning to overhaul this dialog in the near future? That's somewhat of a rhetorical question though, I don't really expect anyone here to answer it. Interestingly the [bug report]("http://bugzilla.gnome.org/show_bug.cgi?id=141154") (read: enhancement request) concerning this issue is from 2004 and the commentary isn't what you'd call booming with activity. 

They're probably doing something, but I'm not very well acquainted with the GNOME/GTK development process (roadmap, release cycle etc.) or how they interact with the outside world so I personally haven't got a clue.

---

### Post by stchman on 2007-06-29
> **MCSE_Crossover said:**
> Ok. My wife and I share the same computer - but we use the same logon. We use Thunderbird for our email program because it has the "Profile Manager" and lets us set up two totally seperate email programs and then we are prompted for which one we want to open when we start Thunderbird.

Well, Thunderbird (and Firefox) for some reason to not offer the ability to preview an image when going through the file browser. So, in Thunderbird, if we are sending an email of our kids and we want to attacha picture, when we click "attach," the only thing that we can see is the text description of the image with no actual thumnail view or image preview.

This seems to be something specific to Mozilla applications. Is there another email program that offers the profile manager ability? I couldn't find it in Evolution or Kmail. Those programs both offer the ability to view thumbnails though.

What is weird is that MS Outlook offers this capability and Evolution is supposed to be an Outlook replacement - yet I was unable to find this feature within Evolution. Hopefully someone can shed some light on this for me.

.

---

### Post by MCSE_Crossover on 2007-06-29
It has to be a combination of Gnome/GTK and mozilla though because when you browse through nautilus, or open office, or even gimp, you get the image preview off to the right.

Here is the related bug [https://bugs.launchpad.net/ubuntu/+s...fox/+bug/89381](https://bugs.launchpad.net/ubuntu/+s...fox/+bug/89381)

And here is a related thread about the file preview: [http://ubuntuforums.org/showthread.php?t=234598&highlight=image+upload+preview](http://ubuntuforums.org/showthread.php?t=234598&highlight=image+upload+preview)

I attached a few pictures as well...but that is neither here nor there...

If you have Thunderbird installed, run "mozilla-thunderbird -P" from the command line. It comes up a profile manager windows were I could select "husband" or "wife" and then choose the appropriate email profile. The third picture I attached is a view of the profile manager window. I am looking for somethng like that.

Here is my thread in regards to the image preview feature and some discussion:

[http://ubuntuforums.org/showthread.php?t=483898](http://ubuntuforums.org/showthread.php?t=483898)

---

### Post by MCSE_Crossover on 2007-06-29
As you can see from the attached pictures as well, this has been fixed some what. It only appears to be a problem within Firefox and Thunderbird. All other programs I seem to be able to view thumbnails or image previews.

---

### Post by Brucevdk on 2007-06-29
> **MCSE_Crossover said:**
> As you can see from the attached pictures as well, this has been fixed some what. It only appears to be a problem within Firefox and Thunderbird. All other programs I seem to be able to view thumbnails or image previews.

Define "all other programs". Anyways, I'm not absolutely sure about this so take everything I say with a grain of salt. But it seems The GIMP uses the [GimpFileDialog]("http://developer.gimp.org/api/2.0/app/GimpFileDialog.html") which as you can see from the object hierarchy is a specialized version of the [GtkFileChooserDialog]("http://developer.gnome.org/doc/API/2.4/gtk/GtkFileChooserDialog.html").  I looked a little bit at the documentation and nowhere I can find that there's a GimpFileDialog in GTK, so I assume it's not in there (but I could be wrong, it's not like I actually looked at the source).

You can find [an example of creating a GtkFileChooserDialog in Python in the PyGTK tutorial]("http://www.pygtk.org/pygtk2tutorial/examples/filechooser.py"). The important bits are:
```

dialog = gtk.FileChooserDialog("Open..",
                               None,
                               gtk.FILE_CHOOSER_ACTION_OPEN,
                               (gtk.STOCK_CANCEL, gtk.RESPONSE_CANCEL,
                                gtk.STOCK_OPEN, gtk.RESPONSE_OK))
response = dialog.run()
dialog.destroy()

```

Not that this really adds anything to the discussion, I guess I'm just rambling. Anyways I'm not sure which dialog Inkscape uses but I think it's safe to assume that Mozilla Thunderbird and Firefox both use the plain GtkFileChooserDialog.

EDIT: I just wanted to make clear that nothing I mention concerning the GtkFileChooserDialog should be interpreted as "whining" or "ranting".

---

