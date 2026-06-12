---
title: "copy-from-time-machine.sh ==== bash: syntax error near unexpected token `&lt;'"
date: 2017-06-06
forum: General Help
---

### Post by earthkid on 2017-06-06
So I am very new to Linux and in trying to figure out how to copy my files from my old MacBook Time Machine external hard drive I discovered this website and this thread:

[https://ubuntuforums.org/showthread.php?t=2193764](https://ubuntuforums.org/showthread.php?t=2193764)

I proceeded to follow the directions outlined in the thread by @coffeecat and when I run the script:

```
sudo ~/Desktop/copy-from-time-machine.sh </media/earthkidred/Black Hole/Backups.backupdb/Stephen Francis’s MacBook/2016-07-05-234414/The Boss Drive/Users/Steve/> </home/earthkidred/TimeMachine/>
```

I get this: 
```

bash: syntax error near unexpected token `<'
```

As I said, I am new to Linux and I am not sure if this is a problem in the copy-from-time-machine.sh code or in something that I am doing.

Here's the link to the code:
[URL="https://gist.github.com/vjt/5183305"]
https://gist.github.com/vjt/5183305[/URL]

Any help would be greatly appreciated. :KS

---

### Post by him610 on 2017-06-06
Hello earthkid, and welcome to the forum,

Can't help with your specific problem, but I can point you to a learning resource, [https://ubuntuforums.org/showthread.php?t=2015424]("https://ubuntuforums.org/showthread.php?t=2015424")

Good luck

---

### Post by steeldriver on 2017-06-06
The < and > characters aren't meant to be typed literally: <source> and <target> are just placeholders for actual paths - so in your case it would be 

```

sudo ~/Desktop/copy-from-time-machine.sh '/media/earthkidred/Black Hole/Backups.backupdb/Stephen Francis&#8217;s MacBook/2016-07-05-234414/The Boss Drive/Users/Steve/' '/home/earthkidred/TimeMachine/'

```

(the quotes are necessary if your paths have whitespace or other special characters - optional otherwise)

---

### Post by earthkid on 2017-06-10
Sweetness.  Thanks man, that did the trick. :guitar:

---

