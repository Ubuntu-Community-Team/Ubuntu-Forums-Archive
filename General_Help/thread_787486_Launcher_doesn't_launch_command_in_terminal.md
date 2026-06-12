---
title: "Launcher doesn't launch command in terminal"
date: 2008-05-08
forum: General Help
---

### Post by A36ykA on 2008-05-08
So I am trying to create a custom launcher on my desktop that runs a script... the script executes perfectly when I manually open the Terminal and type it in, just not when I make the launcher (so I don't have to type it in...). I've tried "gnome-terminal -x [code]", simply [code], and also tried to run the code as an application in terminal, but no luck. Any suggestions? Thanks in advance.

---

### Post by scott_g on 2008-05-08
Do you mind posting what the code is you're trying to run?  Just the [code] portion...

Thanks,
Scott

---

### Post by A36ykA on 2008-05-08
```
xkbcomp /home/ais/Documents/Programs/mirrorboard.xkb $DISPLAY 2>/dev/null
```

---

### Post by A36ykA on 2008-05-08
```
xkbcomp /home/ais/Documents/Programs/mirrorboard.xkb $DISPLAY 2>/dev/null
```

It's the code to flip the keyboard... like a mirror image for one-handed typing.

---

### Post by scott_g on 2008-05-08
Did you try putting the code in a bash script?  Eg:

Create a file like:
```

#!/bin/sh
xkbcomp /home/ais/Documents/Programs/mirrorboard.xkb $DISPLAY 2>/dev/null

```

And place it in say: /home/ais/Documents/Programs/mirrorboard.sh and set up the launcher as a 'Application in Terminal', with the command: ```
sh /home/ais/Documents/Programs/mirrorboard.sh
```

Could work; I don't know why your code wouldn't work in the launcher by itself though...

Thanks,
Scott

---

### Post by A36ykA on 2008-05-08
Thanks for this suggestion - I shall try it now.

---

### Post by A36ykA on 2008-05-09
Awesome!! It worked. I wonder why it didn't work the regular way though... all my other launchers are fine. 

Thank you so much!!

---

