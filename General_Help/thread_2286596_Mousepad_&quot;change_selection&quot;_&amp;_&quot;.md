---
title: "Mousepad: &quot;change selection&quot; &amp; &quot;paste as column&quot;"
date: 2015-07-13
forum: General Help
---

### Post by vasa1 on 2015-07-13
Can someone please explain how **Edit > Change the selection** and **Edit > Paste Special > Paste as Column** work in Mousepad 0.3.0?

---

### Post by Toz on 2015-07-13
Hi Vasa.

This functionality is used for manipulating columnar(?) data. Here is a simple example to illustrate.

Suppose you have two sets of data:
Set 1:
```

0 1 2 3 4 5 6 7 8 9
0 1 2 3 4 5 6 7 8 9
0 1 2 3 4 5 6 7 8 9
0 1 2 3 4 5 6 7 8 9
0 1 2 3 4 5 6 7 8 9
0 1 2 3 4 5 6 7 8 9
0 1 2 3 4 5 6 7 8 9
0 1 2 3 4 5 6 7 8 9
0 1 2 3 4 5 6 7 8 9
0 1 2 3 4 5 6 7 8 9
```

Set 2:
```

a
a
a
a
a
a
a
a
a
a
```
...and you want to replace all of the number 3s in set 1 with the data from set 2.

First, select (starting from before the first #3 to after the last #3) and then Edit -> Change the selection. This should change the selection so that only the column of #3s are selected.

Second, press delete to delete that data.

Thirdly, select the data from set 2 and copy it.

And finally, place your cursor where the first #3 was and Edit -> Paste Special -> Paste as column. The #3s have been replaced by the letter a.

(In fact, you can paste it anywhere as a column, but I was illustrating replacing an existing column).

---

### Post by vasa1 on 2015-07-13
Thanks, Toz. Quite neat :)

---

