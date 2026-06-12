---
title: "change default action sh file"
date: 2013-12-03
forum: General Help
---

### Post by gianluca3 on 2013-12-03
Hello,

I would like to change the default action for a .sh file.

Currently, its default action is to open the file with a text editor. i would like it to become to actually run it. i would like it to behave as if a write:

```

sh filename.sh

```

from shell.

The only way i know to change is to right-clik and select the application from the given list where, however, nothing usefull shows up.

Any suggestion?

To help the discussion, I need this behavior because i'm embedding the script within a pdf document with hyperref package and I want to run the script when clicking on the pdf. In other words, the command

```

\href{run:filename.sh}

```

should run it and not opening in a text editor, as it does now. The file properties has been changed to allow to execute it.

thanks in advance,
gianluca

---

### Post by varunendra on 2013-12-03
Since Ubuntu 13.04, Text Files open up in text editor even if they are scripts or otherwise made executable. To change this-

Open any folder > go to Files > Preferences > Behavior tab > select "**Ask each time**" option under "Executable Text Files" section.

This will revert the default action to what it used to be before 13.04, which is - open a dialogue box that asks whether to open it as a text file, or run it in the background or run it in a terminal, or... cancel the action.

Oh, and Welcome to the forums gianluca3 ! :)

---

### Post by gianluca3 on 2013-12-03
thanks a lot for the reply and sorry, I missed a fundamental information. I still run 12.04 but your information is ok as well.

the default action is now to run the script.

unfortunately, both adobe reader 9 and evince do not behave as expected but i guess noe the issue is not anymore related to the os...

best
g.

---

### Post by varunendra on 2013-12-03
12.04**.3** I guess? Since it contains the [same xorg packages]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") (and so I assume the same settings as well) as 13.04.

Anyway, glad it helped. :)

---

