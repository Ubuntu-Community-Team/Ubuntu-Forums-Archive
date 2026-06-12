---
title: "How to specify folder and file in Thunar Custom Actions for Eiciel"
date: 2015-05-02
forum: General Help
---

### Post by Ralph L on 2015-05-02
I am trying to set up a Thunar Custom Action to right-click launch eiciel on either a folder or a file.  If I set the CA command to ```
eiciel %f
``` a file right-click menu will show eiciel and if I select eiciel, I can see and change acls and extended attributes for the file as I should be able to.  However, if I right-click a folder, the thunar right-click menu will not show eiciel.  If I change the command to be ```
eiciel %d
``` and right-click a folder the right-click menu will still not show eiciel, but if I right-click a file, it will still show eiciel.  Somehow Custom Actions seems to always assume that a file is the only allowable parameter.

Is there any way to get Custom Actions to accept a folder as input???  Is there any way to get Custom Actions to accept either a folder or a file as input???

---

### Post by ajgreeny on 2015-05-02
Let's start with the obvious; have you set the custom action up for folders as well as files in the Appearance conditions tab of the dialogue box as in my screenshot?

---

### Post by Ralph L on 2015-05-02
ajgreeny:  Thank you very much for the response.  Now I really feel dumb.  I completely missed that button.  Yes, that fixed the problem.  Thank you again for your patience.

---

### Post by ajgreeny on 2015-05-02
Great! 
Please mark as SOLVED from the Thread Tools menu at the top of the thread.

---

