---
title: "Having one heck of a time with GREP"
date: 2008-03-14
forum: General Help
---

### Post by elachowitz on 2008-03-14
What I am looking to do is be able to execute this command: ```
epiphany-browser --new-window 'http://localhost/lesson_objectives/test_file.html'
```

I am using the Bluefish IDE which passes a parameter %s (containing my file name) and have tested the following command below:

Assume that %s = 'file:///var/www/lesson_objectives/test_file.html'

```
echo 'file:///var/www/lesson_objectives/test_file.html' | grep -io /[[:alnum:]_]*\.html
```

...which outputs '/test_file.html'

Now, if I can just get this end piece to append to my 'http://localhost/lesson_objectives' + '/test_file.html' I would be good to go!

I have tried using a backreference command to no avail (I am sure what is wrong is my syntax):
```
echo 'file:///var/www/lesson_objectives/test_file.html' | grep -io \(/[[:alnum:]_]*\.html\)\1 | epiphany-browser --new-window 'http://localhost/lesson_objectives'+\1
```

Any help would be great...

Further: I am pretty sure that the first part of the statement should be: cat '%s'

I am just using terminal to test my command and am substituting with echo for now

-el

---

### Post by stylishpants on 2008-03-14
I'm a little bit unclear on what you want, but this command uses backticks to start up epiphany.  I think you should be able to replace the stuff in backticks with %s within bluefish and get what you're after.

I replaced your grep with basename, which is simpler and designed to do exactly this anyway.

```
epiphany-browser --new-window http://localhost/lesson_objectives/`echo 'file:///var/www/lesson_objectives/test_file.html' |xargs basename`
```

Does this do the trick?


Another option:
```

echo 'file:///var/www/lesson_objectives/test_file.html' |xargs basename | xargs -I@  epiphany-browser --new-window http://localhost/lesson_objectives/@

```

---

### Post by elachowitz on 2008-03-14
You rock!

I did however change the command around a little bit (but took your direction in storing the argument using backticks).

I went with:

```
epiphany-browser --new-window http://localhost/`echo '%s' | grep -o lesson_objectives.*`
```

Thanks for your help!!

---

