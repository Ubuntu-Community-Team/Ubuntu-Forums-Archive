---
title: "error 404"
date: 2012-11-23
forum: General Help
---

### Post by cdwg9983 on 2012-11-23
Hi,
I am trying to create a webpage, but it isn't letting me.  Here's what I've done:  Through terminal, i entered "sudo vi test.html" to create test.html in the htdocs folder.  When brought to the coding screen, i started typing, but nothing has been showing up.  After about one word, it starts to show up.  I finish the code and then I'm not sure what to do after that.  I typed in [http://localhost/test.html](http://localhost/test.html) and it displays a page that says error 404.  Then, I looked into the htdocs folder and there was nothing in it.  I tried it again, entering "sudo vi test.html" to create a webpage in htdocs again and received a message, saying that that file was already created and wasn't completed.  How can i fix this?  I'm really just looking to find out how to create a webpage, but the issue with terminal is making me think that it's an issue with ubuntu rather than xampp.

Thanks

---

### Post by sandyd on 2012-11-23
By default, when you open a file in VI, it is in "view mode".
To start editing, hit 'i'

When your done, press [ESC], and then type
```

:wq
```(write and quit) to write and quit.

Sometimes, you have to press [ESC] twice.
Here is a nice cheat sheet on VI commands [http://www.smashingmagazine.com/2010/05/03/vi-editor-linux-terminal-cheat-sheet-pdf/](http://www.smashingmagazine.com/2010/05/03/vi-editor-linux-terminal-cheat-sheet-pdf/)

If you find VI hard to use, try Nano or VIM.

Regards,

---

### Post by cdwg9983 on 2012-11-23
Thanks so much :)!
It works!

---

