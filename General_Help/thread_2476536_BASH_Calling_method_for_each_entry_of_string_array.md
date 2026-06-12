---
title: "BASH: Calling method for each entry of string array"
date: 2022-06-29
forum: General Help
---

### Post by fritzbender on 2022-06-29
Hi there,

I saw that functions have been called several times in BASH using brackets. I wanted to do the same thing, so calling my function my_func three times and passing another entry of the string array each time:

```

my_func() {
  do_something_with $1
}
my_func { "a" "b" "c"}

```

but the method is only called once. What am I doing wrong? Did I misunderstood the bracket pattern? Don't get me wrong, I know how to create and pass an array in BASH I just wanted to use that new pattern.

Thanks

---

### Post by The Cog on 2022-06-29
[https://opensource.com/article/18/5/you-dont-know-bash-intro-bash-arrays](https://opensource.com/article/18/5/you-dont-know-bash-intro-bash-arrays)
```
my_func() {
    echo Working on $1...
}
a=(one two three)
for v in ${a[@]} ; do my_func $v ; done
```

---

### Post by Holger_Gehrke on 2022-06-29
Could you give us an example of where you've seen that ? I've written and read shell scripts for quite some time and never came across something like you describe. There's also no mention of any capability like that in the manual that I can find.

Holger

---

### Post by fritzbender on 2022-06-29
Ah, I found it. It's called the brace expression and can be used like this:

```
echo Front-{A,B,C}-Back
```

which results in: Front-A-Back Front-B-Back Front-C-Back

Sorry for my confusing question.

---

