---
title: "Audio Recorder App will not record more than 58 minutes"
date: 2020-04-06
forum: General Help
---

### Post by Old Jimma on 2020-04-06
Hello Community:

I'm using the Audio Recorder app to record radio shows that air after I go to bed at night.

Here re the commands I use: in the Audio Recorder command box:

```
stop after  66min
```

The check box to the left of the command box is checked and it ignores this command, and will records 58 minutes... I don't know why it records only 58 minutes and not 66.

Can somebody help me with this?

Thanks,
Old Jimma

---

### Post by kneutron on 2020-04-07
a) How much free space do you have on disk where you're saving the audio files

b) try filing a bugreport ?

---

### Post by Old Jimma on 2020-04-19
Folks:

Audio recorder commands must be in hour minute and second format.

In the command box of audio recorder, it is a "error" to use:

> stop after  66min

Audio recorer  1 thru 59 as valid entries for minutes. Therefore, 66min will not work. However, 1hr 6 min will:

The correct command would be
> stop after  1hr 6min

Old Jimma

---

