---
title: "Search string for programme via get-iplayer, how ?"
date: 2016-05-02
forum: General Help
---

### Post by grey1beard on 2016-05-02
i'm trying to search iplayer radio in terminal for a programme **Radio 3 Lunchtime Concert  BBC Proms Australia 2016**.
I've been typing in* get-iplayer --type=radio*  , then a keyword.
Tried lots of different keywords, including just pasting in the url of the iplayer page (which I use to grab TV programmes), but the basic problem for me is that I don't know how to write a string(?) of words in terminal, to refine a search.
Grateful for instruction.

John

---

### Post by grey1beard on 2016-05-02
Found the quotes around the string seems to work, but if I put in "lunchtime concert" in quotes, it only throws up the Shakespeare 400 programmes, not the Australian proms :(

tried lots of other variations, but can make no progress.
John

---

### Post by grey1beard on 2016-05-02
Is there a way of using just the pid for a radio programme ?

If not, then I give up !
John

---

### Post by dragonfly41 on 2016-05-02
Although I'm not a user of this tool, if you run the command get-iplayer --type=radio --help
and read the output
it seems that the search pattern has to be in REGEX (regular expression).

Perhaps try creating a regex search string and validate with a regex GUI from Software Centre.

---

### Post by howefield on 2016-05-02
Don't see this particular broadcast by searching despite it being available, however
```

 get_iplayer --pid=b07740hh --type=radio
 get_iplayer --pid=b07740j1 --type=radio
 get_iplayer --pid=b07740jb --type=radio
 get_iplayer --pid=b07740jm --type=radio
```

should get you to each of the 4 parts ?

---

### Post by grey1beard on 2016-05-02
Hi howefield, and thanks.
Works, and am now downloading :)

John

---

### Post by howefield on 2016-05-02
You're welcome, obviously the commands can be tweaked to suit the bitrate and format that you want to end up with.

---

