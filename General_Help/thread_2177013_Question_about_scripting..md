---
title: "Question about scripting."
date: 2013-09-26
forum: General Help
---

### Post by rolltide101x on 2013-09-26
```
read -p "Are you happy? (y/n) " QUESTION
if [ "$QUESTION" = "y" ]; then
wine happy.exe
else
 "go to line 21"
 exit
```

What would I use to obtain "go to line 21" in this situation (I obviously made it up lol)

---

### Post by ian-weisser on 2013-09-27
echo
fi

---

### Post by Kirk Schnable on 2013-09-27
Why in the world would you want to use a goto statement?  Bash is so much more versatile than that.

One approach which comes to mind is instead of using a goto, write a function to do what you want.

eg.
```
sad(){
echo "Don't be sad...."
wine domystuff.exe
}
```

Below that function declaration, then your code would look like:
```
read -p "Are you happy? (y/n) " QUESTIONif [ "$QUESTION" = "y" ]; then
wine happy.exe
else
 sad
 exit

```

Please note: Functions must be declared BEFORE they are used, so you should write your functions toward the top of your script.

Does that help?

---

### Post by rolltide101x on 2013-10-02
Thanks, that helps a lot! Thank both of you for your time

---

