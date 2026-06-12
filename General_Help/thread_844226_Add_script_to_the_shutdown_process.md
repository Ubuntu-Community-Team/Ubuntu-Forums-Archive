---
title: "Add script to the shutdown process"
date: 2008-06-29
forum: General Help
---

### Post by Ballena on 2008-06-29
Hello.

I want to make a script or add a part to an existing script that checks if there are any screen sessions running and if so send a quit message to them. But where do I find the shutdown scripts or how do I make a script run on shutdown? It's something about run levels right?

All answers are appreciated!
Thanks /Ballena

---

### Post by HalPomeranz on 2008-06-29
Create your shell script in /etc/init.d-- let's suppose for purposes of this example you're going to call the script "screenshutdown".  Then you have to make links to the script in the various /etc/rc?.d directories:

```

for d in /etc/rc?.d; do
    ln -s /etc/init.d/screenshutdown $d/S99screenshutdown
done

```

The link to the script in the approrpriate /etc/rc?.d directory is what causes it to be executed when the system shuts down.

You might find this thread helpful for explaining the role of these various directories in the system boot process:

[http://ubuntuforums.org/showpost.php?p=5269768&postcount=2](http://ubuntuforums.org/showpost.php?p=5269768&postcount=2)

---

