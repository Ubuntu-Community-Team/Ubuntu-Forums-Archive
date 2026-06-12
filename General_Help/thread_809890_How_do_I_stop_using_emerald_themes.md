---
title: "How do I stop using emerald themes?"
date: 2008-05-27
forum: General Help
---

### Post by JaggedOne on 2008-05-27
I installed emerald and now I want to stop using it. I used the comand sudo emerald --replace when I insatlled emerald to get its themes to appear. Now I have uninstalled emerald and it still shows emerald themes. How do I get back to the default ubuntu theme manager?

---

### Post by overdrank on 2008-05-27
> **JaggedOne said:**
> I installed emerald and now I want to stop using it. I used the comand sudo emerald --replace when I insatlled emerald to get its themes to appear. Now I have uninstalled emerald and it still shows emerald themes. How do I get back to the default ubuntu theme manager?

HI and that would be ```
metacity --replace
```
I stand corrected WindowsSucks is correct as I did not read the post correctly. :(

---

### Post by klange on 2008-05-27
> **overdrank said:**
> HI and that would be ```
metacity --replace
```

No. That would kill Compiz.

```
gtk-window-decorator --replace
```
is what you want.
And if you removed Emerald, it shouldn't be there to draw your decorations...

---

### Post by JaggedOne on 2008-05-27
> **WindowsSucks said:**
> No. That would kill Compiz.

```
gtk-window-decorator --replace
```
is what you want.
And if you removed Emerald, it shouldn't be there to draw your decorations...

Somehow it is.

---

### Post by Forlong on 2008-05-28
Did running ```
gtk-window-decorator --replace
``` fix it for you?

---

### Post by SomeGuyDude on 2008-05-28
```
metacity --replace
```

```
killall emerald
```

```
compiz --replace
```

That always did it for me.

---

