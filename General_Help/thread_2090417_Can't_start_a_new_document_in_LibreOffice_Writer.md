---
title: "|Can't start a new document in LibreOffice Writer"
date: 2012-12-02
forum: General Help
---

### Post by t0p on 2012-12-02
I'm having a very bizarre problem here.  When I start LibreOffice Writer, it doesn't open with a new blank document.  The document is called Untitled 1, but its contents are from a previous document - specifically a series of images that I pasted into a previous document.  And when I hit File > New > Text Document, it creates a "new" document, called Untitled 2, which also has the contents of this previous document.  So, I have to delete the series of images before I can create my new document.

Obviously, this isn't supposed to happen.  Any ideas why it's happening and how to stop it?  I'm using LibreOffice 3 on Ubuntu 12.04.

Cheers.

---

### Post by vanadium on 2012-12-02
Look into the dialog "File - Templates - Organize". It looks as if a file has been defined as your default template. In the dialog, you would then need to find the dialog in the left pane, highlight the file name, and use the button "commands". With a custom default template highlighted, this button provides the option "Reset default template". This would reset the template back to the "factory default".

You may also create your custom template and then "actively" (rather than by accident) install it as your default template using that dialog.

---

### Post by t0p on 2012-12-02
Thank you vanadium, all is right again. I am very grateful for your advice.

---

