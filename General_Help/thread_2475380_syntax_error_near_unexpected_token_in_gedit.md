---
title: "syntax error near unexpected token in gedit"
date: 2022-05-25
forum: General Help
---

### Post by chat-4432 on 2022-05-25
I try to use gedit as python coding
but  when I need to run Hello world it shows
```
./helloworld.sh: line 1: syntax error near unexpected token `"Hello world"'
./helloworld.sh: line 1: `print("Hello world")'



```
it does not show only Hello world
I also change .sh to .py but show the same error.
what should I do??

---

### Post by Impavidus on 2022-05-25
You probably missed the first line, declaring that the script must be interpreted as python. Without that, the system tries to run it with the default interpreter, which, I think, is dash.```
#!/usr/bin/python3
print("Hello world!")
```

Filename extensions don't matter. It's customary to use the .py extension for python scripts, but not mandatory. The first line of the script is what counts.

---

