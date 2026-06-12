---
title: "Case insensitive tab completion?"
date: 2007-11-04
forum: General Help
---

### Post by khughitt on 2007-11-04
Heya,

I was reading a magazine the other day, either Linux format or Linux pro I believe, and there was a suggestion for a way to setup bash to have case-insensitive tab completion. It involved using some command which I can't remember now, but I've never used the command before.

Anyone know how to do this, or what the command is?

Thanks!

---

### Post by bingoUV on 2007-11-04
complete is a bash builtin command which defines which options to list to people when they hit tab. You might have to use it. For examples, see  /etc/bash_completion. For documentation, see 
```

man complete

```

and search for the section on complete. I am not sure the existing command is powerful enough to do what you suggest, but then, I never tried. 

good luck

EDIT

The builtin seems all-powerful , sorry, I underestimated it.

---

### Post by khughitt on 2007-11-04
Thanks,

that wasn't quite the command I was looking for, but I will look into that. Anyone know of any other ways?

---

### Post by thetictacaddict on 2008-04-09
I was looking for an answer to the same question, and I found it somewhere else.  I thought it might help someone to mention it here even though the thread is a bit old.

To get case-insensitive tab completion in bash, add the line

```
set completion-ignore-case on
```

to the file /etc/inputrc

---

### Post by khughitt on 2008-04-12
Thanks :)

---

