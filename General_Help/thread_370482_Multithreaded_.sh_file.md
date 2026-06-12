---
title: "Multithreaded .sh file"
date: 2007-02-25
forum: General Help
---

### Post by chocomoojuice on 2007-02-25
Note:  Sorry if I'm using the wrong term to describe what I want to do, I'm relatively new to programming.

My intension is to run 2 tribes servers (tribes is a game), and instead of going through the terminal and cd-ing to each directory and entering the command repeatidly, I'd like to be able to simply execute a .sh file.  However, I'm running 2 different instances of wine for each server, so the second instance of wine won't start until I close the first instance.  So I currently need to have 2 seperate .sh files, one for each server:

```
cd /home/james/.wine/drive_c/Dynamix/Tribes
wine InfiniteSpawn.exe *tribes -mod Meltdown -dedicated
```and

```
cd /home/james/.wine/drive_c/Dynamix/Tribes
wine InfiniteSpawn.exe *tribes -mod MeltdownClassic -dedicated
```Is there any way I can consolidate these two .sh files into 1 so that it will start both servers?

Thanks in advance,
James

---

### Post by PriceChild on 2007-02-25
```
cd /home/james/.wine/drive_c/Dynamix/Tribes
wine InfiniteSpawn.exe *tribes -mod Meltdown -dedicated &&  wine InfiniteSpawn.exe *tribes -mod MeltdownClassic -dedicated
```Perhaps?

---

### Post by chocomoojuice on 2007-02-25
> ```
cd /home/james/.wine/drive_c/Dynamix/Tribes
wine InfiniteSpawn.exe *tribes -mod Meltdown -dedicated &&  wine InfiniteSpawn.exe *tribes -mod MeltdownClassic -dedicated
```
Perhaps?

When I try this, it only opens one of the two servers (the first one listed in your line of code with tag Meltdown).  I tried running the .sh file in the terimnal to look for any errors, but found none.  Thanks for the help thus far, but have you any more suggestions?

---

### Post by PriceChild on 2007-02-25
Hehe I'm not the best guy to answer... tried with just one & maybe?

---

### Post by chocomoojuice on 2007-02-25
> Hehe I'm not the best guy to answer... tried with just one & maybe?
Yay, that worked!

Thank you!

---

### Post by PriceChild on 2007-02-26
Wooo :) I'll remember that for later.

*marks as resolved*

---

