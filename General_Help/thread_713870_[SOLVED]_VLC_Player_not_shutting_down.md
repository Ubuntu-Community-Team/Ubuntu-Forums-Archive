---
title: "[SOLVED] VLC Player not shutting down"
date: 2008-03-03
forum: General Help
---

### Post by Rytron on 2008-03-03
Hi,

I'm not sure if this is the correct place for this thread.

I use the great VLC player.
I used this in windows xp without a problem.
However when I use it in ubuntu I notice that when I close vlc the file(movie,music,etc) keeps playing enen though I have ended vlc.
Is there a way to shut down vlc player.
At present the only way around this is to log off and log back in again - very awkward.

Any help appreciated.

Also concerning this - I know that you can press ctr + alt + backspace key to log out - thus sometimes saving you in a jam.
Is there a method to display all running processes in Ubuntu? System monitor does not seem to show vlc when I close it even though the music is still playing.

Thanks.

---

### Post by kesman on 2008-03-03
How did you install VLC? You can kill any process from terminal by first looking for all running processes with
```

ps -A |more

```

and when you see something related to vlc, you can kill it with
```

sudo kill <number of the process>

```
without the < and >:s

---

### Post by Rytron on 2008-03-03
thanks kesman.

I installed vlc via the add/remove tool.

---

### Post by kesman on 2008-03-03
And have you added the medibuntu software source? I think it may have never versions of media players which correct these kind of bugs.

---

### Post by Rytron on 2008-03-03
I tried code below, it worked. Thanks.

How do I install the medibuntu software?


```

ps -A |more

```

and when you see something related to vlc, you can kill it with
```

sudo kill <number of the process>

```

---

### Post by kesman on 2008-03-03
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

You should read trough that, it has plenty of information of everything you need in ubuntu.

---

### Post by Rytron on 2008-03-03
[B][I][COLOR="Navy"]hi kesman,
thanks for your help.
I used your code - works a treat.

How do I mark the thread solved? - Do I just put solved here?

...ah just got it under thread tools drop down list at the top of the page. cheers.

:)[/COLOR][/I][/B]

---

### Post by k66473 on 2008-04-17
hix. I encountered this trouble too.
Close VLC and the songs still continue go on. (open directory troubles)
I must kill vlc process in system monitor.

---

