---
title: "MATLAB needs custom launch, but it only works in Terminal"
date: 2007-10-18
forum: General Help
---

### Post by kombucha on 2007-10-18
So after a little research I learned that Compiz and MATLAB only play nicely together if MATLAB is launched using the command ```
export AWT_TOOLKIT=MToolkit ; /home/eli/MATLAB/bin/matlab
``` I tried it in terminal, and it worked great - all of the basic toolbars were now visible.

However, this is the only way I can get it to work. I tried putting the same command in a panel launcher, and the MATLAB splash comes up but that's it. I tried making a desktop script and running that, but the same thing happens. What the hell is going on? Why is it so picky as to where I invoke this code from? Or am I missing something crucial about the difference between a script and running from the terminal?

Thanks!

---

### Post by spooner on 2007-10-18
Wow, that worked great... matlab and desktop effects.
To create a launcher you are going to need a script. I have a bin directory and inside that I have a text file called matlab-alt.sh.
In that file there is: -
```

#!/bin/bash
unset LANG
export AWT_TOOLKIT=MToolkit
matlab -desktop

```

I had a problem with changing the settings in matlab (do to strange install)... they wouldn't save and the unset LANG solves that problem. You probably just need the other three lines. Then just create a launcher that points to the script.

---

### Post by kombucha on 2007-10-18
Thanks, that worked perfectly :)

---

### Post by 00l0 on 2007-10-23
> **spooner said:**
> Wow, that worked great... matlab and desktop effects.
To create a launcher you are going to need a script. I have a bin directory and inside that I have a text file called matlab-alt.sh.
In that file there is: -
```

#!/bin/bash
unset LANG
export AWT_TOOLKIT=MToolkit
matlab -desktop

```

I had a problem with changing the settings in matlab (do to strange install)... they wouldn't save and the unset LANG solves that problem. You probably just need the other three lines. Then just create a launcher that points to the script.

That worked just like a charm, i really THank you very much
 ;D

---

### Post by antonio.spadim on 2007-10-30
I'm trying to do this script work but it insists in print the message:

  Detalhes: Falha ao executar processo filho "/home/midaps/prgs/matlab7/bin/matlab-alt.sh" (Permissão negada)

I'll try in english,
  Details: Execute process failed .... (Permission denied)

How can I solve this? or 

Could you write some step-by-step tutorial to create the file, build this script, load it, etc...? 

Thanks,
Antonio

---

### Post by mali2297 on 2007-10-30
> **antonio.spadim said:**
> I'm trying to do this script work but it insists in print the message:

  Detalhes: Falha ao executar processo filho "/home/midaps/prgs/matlab7/bin/matlab-alt.sh" (Permissão negada)

I'll try in english,
  Details: Execute process failed .... (Permission denied)

How can I solve this? or 

Could you write some step-by-step tutorial to create the file, build this script, load it, etc...? 

Thanks,
Antonio

Have you made the script executable?
```

chmod +x /home/midaps/prgs/matlab7/bin/matlab-alt.sh
/home/midaps/prgs/matlab7/bin/matlab-alt.sh

```

---

### Post by antonio.spadim on 2007-10-30
Thanks man,

   I did it, and now, it's working!!!! :) 

Linux Rocks :guitar:

---

