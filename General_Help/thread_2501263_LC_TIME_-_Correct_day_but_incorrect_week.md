---
title: "LC_TIME - Correct day but incorrect week"
date: 2024-09-30
forum: General Help
---

### Post by oknitter on 2024-09-30
Hi Team,
for simple backup reasons I'm adding calendar week and day to the stored backup image filename. I prefer Monday as first day of week.
For that my LC_TIME is set to:
```
LC_TIME=de_DE.UTF-8
```

this is the filename composition
```
PI5_KW`date +"%U"`_"$(date +%u)".img
```

but any backup file is using correct day of week - but incorrect week number..
```
Sep 28 PI5_KW38_6.img
Sep 29 PI5_KW[COLOR=#ff0000]39[/COLOR]_7.img
Sep 30 PI5_KW39_1.img
```

red marked week number should still be 38 as it is Sunday.

According to what the date returns, it appears to me that day of week follows locale but week number does not and still starts on Sunday. Any thoughts on that?

-----

Solved with this [https://ubuntuforums.org/showthread.php?t=2501263&p=14207812#post14207812](https://ubuntuforums.org/showthread.php?t=2501263&p=14207812#post14207812)

---

### Post by ActionParsnip on 2024-09-30
```

--iso-8601

```
Has Monday as the first day of the week, possibly add that

---

### Post by oknitter on 2024-10-01
> **ActionParsnip said:**
> ```

--iso-8601

```
Has Monday as the first day of the week, possibly add that
Not sure I understand....
Day of week appears to be okay but the week shouldnt start on Sunday.

And - how shall I incorporate the option into my filename?

---

### Post by oknitter on 2024-10-01
UPDATE:
Got it... rather than using %U, it should be %V as this is ISO week number format and starts with Monday

---

### Post by ActionParsnip on 2024-10-01
Nice one. Please mark as solved if the issue is no more :)

---

