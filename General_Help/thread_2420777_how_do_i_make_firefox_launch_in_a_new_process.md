---
title: "how do i make firefox launch in a new process?"
date: 2019-06-10
forum: General Help
---

### Post by Skaperen on 2019-06-10
i would like to know how to make firefox start in a new process instead of trying to connect to an existing process.  i have been trying the command line argument  --no-remote but it still tries to connect.

---

### Post by Xian on 2019-06-10
AFAIK you will need to choose a different profile since the one in the first process is locked when in use.

This would require the use of the command line -p option.

For example:
```
firefox.exe -no-remote -p profilename
```

---

### Post by Skaperen on 2019-06-10
that worked, although it ignored the profile name and needed me to type it in. that defeats my intent to launch a firefox browser window in a separate process for each forum i visit.  it is now running in PIDs 16549 (here) and 16877 (xfce forum).

---

### Post by SantaFe on 2019-06-11
You might want to watch this video by TuxDigital: [https://www.youtube.com/watch?v=bGTBH9yr8uw](https://www.youtube.com/watch?v=bGTBH9yr8uw)

In it he does talk about using Multi-Account Containers (Container Tabs) which, assuming you add the container tabs extensions he mentions, will allow you to have different tabs open in the same profile but with different logins.

I know it's not a whole new instance of Firefox, but might achieve the same results?  Hope it helps. ;)

---

