---
title: "bash: !&quot;: event not found"
date: 2006-12-19
forum: General Help
---

### Post by ububuL on 2006-12-19
```
$echo "hello world!" | tr '!' ' '
bash: !": event not found
```

Can someone help me with this? Thanks.

---

### Post by Azakus on 2006-12-19
Don't use quotes. I'm not really sure what they do, but they start something else in bash, just like ` corresponds to a command. Example (output from terminal)
```
dan@dan-desktop:~$ '
> exit
> #nothing happens
> 

```
You don't need them anyway.

---

### Post by hikaricore on 2006-12-19
aye:

echo hello world! | tr '!' ' '

works just fine :/

I spent like 10 minutes tryin to figure out a special character code for ! so you could use it.

Overlooked the obvious :P

---

### Post by comp9z on 2006-12-19
echo \"hello world! | tr '!' '\"'  ? 

It seems the exclamation mark confuses bash or something

---

### Post by hal10000 on 2006-12-19
echo 'Hello World!' | tr '!' ' '

---

### Post by ububuL on 2006-12-20
> **hal10000 said:**
> echo 'Hello World!' | tr '!' ' '

Thank you all for responding. I still don't understand why the double quote doesn't work because it is right. Any more explanation.;)

---

### Post by holdinout on 2006-12-20
What does this command do?

---

### Post by ububuL on 2006-12-20
> **holdinout said:**
> What does this command do?

It replaces ! with a space. You can see that yourself by typing the following
```
echo 'hello, world!' | tr '!' ' '
```

---

### Post by po0f on 2006-12-20
In Bash, a single quote (') is referred to as a strong quote, and a double quote (") is referred to as a weak quote.  Special characters aren't interpreted in a strong quote (! is a command that refers to the history in Bash IIRC), which is why you could single quote it and get the desired result.  Variables, special characters and the like are interpreted in a double quote though.

---

### Post by hikaricore on 2006-12-20
Simple yet effective way to start learning bash parsing  :)  You can't beat hello world.  Lol

Reminds me of my first hello world program in basica on my old tandy ^.^

---

