---
title: "anti virus"
date: 2007-06-20
forum: General Help
---

### Post by mr.farenheit on 2007-06-20
this probably might be a dumb question but should i even bother with an anti virus? i never have before neither windows or linux. i'm just curious as to with the recent growth in population of linux users that it soon might become a target for malwares.

---

### Post by merlinus on 2007-06-20
Might be useful if you share or send files to windows users such as word documents.

avg works well.

-merlin

---

### Post by mr.farenheit on 2007-06-20
i tried avg before and was impressed. forgot it worked on linux too. guess i'll give that a try when it comes down to it

---

### Post by slimdog360 on 2007-06-20
Ive never had a virus or anything while running linux for over a year now with out an antivirus, I think that speaks for its self. I still do use a firewall though.

---

### Post by scrooge_74 on 2007-06-20
I have taken the policy of if you get infected is your own fault not mine so I dont use and antivirus, I usually was  very responsabile when I used windows and I got very few viruses.  So since i am free of that  I dont use antivirus anymore.

Nice Avatar by the way

---

### Post by i0Null on 2007-06-22
I personally don't need anti virus. However if you opt to use AVG, you may want to disable that annoying license popup when you start the GUI. You can do that in the current version (7.5.47) by commenting out a line in "/opt/grisoft/avggui/prog/mainview.py" 

From:
```

135                 self.__manage_license(avg_info.avgscan_output)

```

To:
```

135                 #self.__manage_license(avg_info.avgscan_output)

```

---

