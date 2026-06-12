---
title: "Matlab axis label problem on ubuntu edgy"
date: 2006-11-26
forum: General Help
---

### Post by The_Noise on 2006-11-26
Hi to the forum,

since I've upgrated from dapper to edgy matlab doesn't shows the axis label anymore. Furthermore, if I select for example "Save as" from the "File" menu of a figure window I get the dialog window with the various widgets but without any font.

I've tried both matlab 7.1 and 7.3. If I run the same installation of matlab remotely (from another machine) then matlab shows correctly the axis label and the font in the various dialogs of the figure windows. So I think it's an X server problem.

Does someone use matlab on edgy and have encountered such a problem?

Any hint  for a possible solution?

Many thanks,

  ~ The Noise

---

### Post by zgornel on 2006-11-26
Try reinstalling it...

---

### Post by buttari on 2006-11-26
> **The_Noise said:**
> Hi to the forum,

since I've upgrated from dapper to edgy matlab doesn't shows the axis label anymore. Furthermore, if I select for example "Save as" from the "File" menu of a figure window I get the dialog window with the various widgets but without any font.

I've tried both matlab 7.1 and 7.3. If I run the same installation of matlab remotely (from another machine) then matlab shows correctly the axis label and the font in the various dialogs of the figure windows. So I think it's an X server problem.

Does someone use matlab on edgy and have encountered such a problem?

Any hint  for a possible solution?

Many thanks,

  ~ The Noise


Hi,
what happens if you run matlab without the gui? Try running 
```

$ matlab -nojvm

```

and see if you still have the problem with the axis label. I already recomended using matlab without gui in a couple of other posts: the matlab gui in linux is simply stuffed with bugs of all kinds. Moreover I find the -nojvm version much faster.
Regards

Alfredo

---

### Post by The_Noise on 2006-11-27
Thanks for the answers.

I've jet tried to reinstall matlab and to run it without the java vm but without any luck.

Running "matlab -nojvm" it's much faster, but if if I do a plot, a figure windows is opened but without any axis label (as with the gui version).

Any other tip?.

Thanks,

  ~ The Noise

---

### Post by The_Noise on 2006-11-27
I've found the problem.

Matlab does not support UTF8. We have to launch matlab with the non utf8 locale. In my case

 $ LANG=it_IT matlab

solves the problem.

Thanks again.

Ciao,

  ~ The Noise

---

### Post by The_Noise on 2006-11-28
> **The_Noise said:**
> I've found the problem.

Matlab does not support UTF8. We have to launch matlab with the non utf8 locale. In my case

 $ LANG=it_IT matlab

solves the problem.

Thanks again.

Ciao,

  ~ The Noise

That didn't solved the whole problem unfortunately.

The axis label are shown using this workaround but still the "Save as" and the "Open" dialogs of the figure windows are shown without fonts (I can see only the filename and the path in there, but no file list or button text or other).

Does someone have some suggestion?


Thanks,

  ~ The Noise

---

