---
title: "How can I change the default ls by ls -l?"
date: 2008-04-06
forum: General Help
---

### Post by Bunghi on 2008-04-06
Hi.

By default, Ubuntu uses the simple ls style, but I almost always use ls -l. Is there any way to change the default ls by ls-l so when I type ls it shows to me like ls -l ?

Thanks!

---

### Post by jocko on 2008-04-06
you could set up an alias like this:
```
gedit ~/.bashrc
```paste this to the end of the file:
```
alias ls='ls -l --color=auto'
```There may already be a line looking like this:
```
 alias ls='ls --color=auto'
```
just put the '-l' in there (without the quotes).




Log out and log in again to get it to work.

---

### Post by brian_p on 2008-04-06
> **Bunghi said:**
> Hi.

By default, Ubuntu uses the simple ls style, but I almost always use ls -l. Is there any way to change the default ls by ls-l so when I type ls it shows to me like ls -l ?

Thanks!

To add to jocko's suggestion, you could also have

```
alias ll='ls -l'
```

if you wanted to keep ls for the odd occasion you find it useful, Actually, that code might already be in your .bashrc but commented out.

---

### Post by Bunghi on 2008-04-06
That worked. Thanks!

---

### Post by bodhi.zazen on 2008-04-06
> **brian_p said:**
> To add to jocko's suggestion, you could also have

```
alias ll='ls -l'
```

if you wanted to keep ls for the odd occasion you find it useful, Actually, that code might already be in your .bashrc but commented out.

If you want to run a command you have aliases, you can do so with single quotes.

```
'ls'
```

---

### Post by brian_p on 2008-04-06
> **bodhi.zazen said:**
> If you want to run a command you have aliases, you can do so with single quotes.

```
'ls'
```

Thanks for that. Bash thinks of everything. Four keystrokes though!

---

