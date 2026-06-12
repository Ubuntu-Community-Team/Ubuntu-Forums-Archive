---
title: "How to avoid multiple application instances?"
date: 2005-08-13
forum: General Help
---

### Post by moraes on 2005-08-13
Hello. :grin: 

I would like to avoid jEdit to open another window when I click a PHP file (jEdit is the default application to open PHP files). It should use the same started instance, if there is one. Intead, for every file I click it opens another jEdit instance.

Also, I want to bypass the prompt "Do you want to run "index.php", or display its contents?", and just open PHP files directly with jEdit when I click on them.

Can anyone give me some tips?

thanks,
moraes

---

### Post by moraes on 2005-08-14
Bump! :???: 

Hmmm. Noone can give me a tip?

m.

---

### Post by moraes on 2005-08-28
I found a solution! :D

1. Open /usr/bin/jedit with a text editor.

2. Add **-reuseview** after the program is called, like this:
```

if [ -e /usr/lib/j2re1.3/bin/java ]; then
	exec /usr/lib/j2re1.3/bin/java -mx${JAVA_HEAP_SIZE}m ${JEDIT} -jar "/usr/share/jedit/jedit.jar" -reuseview $@
else
	exec java -mx${JAVA_HEAP_SIZE}m ${JEDIT} -jar "/usr/share/jedit/jedit.jar" -reuseview $@
fi
```

3. Done! Perfect! Whooohoooo! :D

---

