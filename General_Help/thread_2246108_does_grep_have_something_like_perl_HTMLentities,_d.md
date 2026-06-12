---
title: "does grep have something like perl HTML::entities, decode_entities"
date: 2014-09-28
forum: General Help
---

### Post by vasa1 on 2014-09-28
I came across> If you have libwww-perl installed, you can use the decode_entities function from HTML::Entities. **This will make HTML entities like  , ", etc. look prettier**.
```
curl -u username --silent "https://mail.google.com/mail/feed/atom" | perl -MHTML::Entities -ne 'print "\t" if /<name>/; print decode_entities($2)."\n" if /<(title|name)>(.*)<\/\1>/;'
```and> LOL, and of course my comments show them as their decoded form. I am of course referring to the & nbsp; & quot;, etc. (I put a space between the ampersand and the rest of the entity.as comments posted by "archtaku" over here: [http://www.commandlinefu.com/commands/view/3386/check-your-unread-gmail-from-the-command-line#comment](http://www.commandlinefu.com/commands/view/3386/check-your-unread-gmail-from-the-command-line#comment)

Does grep have an equivalent for what I've put in **bold**?

---

### Post by Lars Noodén on 2014-09-28
grep only finds patterns and cannot do substitutions.   awk could do substitutions, but then you'd have to code patterns for all the [HTML entities](http://www.w3.org/TR/html4/sgml/entities.html), entities which you get 'free' by adding *-MHTML::Entities* to your one-liner perl script.  

Perl is really useful and easy for that kind of text processing.

---

### Post by vasa1 on 2014-09-28
Thanks for explaining!

libwww-perl is installed on my system. I don't know if it's there by default or not. My limited exposure to perl has been to a little of "perl -pie". Hoping to pick up a little more as time flies by.

---

### Post by vasa1 on 2014-09-29
Well, I just found out about [GNU recode]("http://unix.stackexchange.com/a/149252"). Now, I have this:```
curl -u username:password --silent "https://mail.google.com/mail/feed/atom" | recode xml | sed 's/></>\n</g' | grep -e fullcount -e title -e summary -e name
```I'm just a little bit worried about having multiple pipes. I read somewhere that commands which incorporate pipes don't always work from left to right.

---

### Post by Lars Noodén on 2014-09-29
Pipes feed from left to right.  Output from the left goes in as input to the next one on the right all the way down the chain.   ( Maybe you were thinking also of redirects using < and > instead? )

One thing to consider is that if you launch curl like you have done

```

curl -u username:password ...

```

then the username and the password will show up in the list of system processes and anyone can see the password using ps while curl is running.  You might be able to use [expect](http://manpages.ubuntu.com/manpages/trusty/en/man1/expect.1.html) or something like it to keep the password hidden.  Also make sure that any files with the password are in a directory owned by you and set 700 and the file itself is 600.

---

### Post by vasa1 on 2014-09-29
> **Lars Noodén said:**
> Pipes feed from left to right.  Output from the left goes in as input to the next one on the right all the way down the chain.   ( Maybe you were thinking also of redirects using < and > instead? )
No, it's about pipes. Here's [an answer to the question: In what order do piped commands run?]("http://unix.stackexchange.com/a/37597") and that gets me concerned over having several pipes.

> **Lars Noodén said:**
> One thing to consider is that if you launch curl like you have done

```

curl -u username:password ...

```

then the username and the password will show up in the list of system processes and anyone can see the password using ps while curl is running.  You might be able to use [expect](http://manpages.ubuntu.com/manpages/trusty/en/man1/expect.1.html) or something like it to keep the password hidden.  Also make sure that any files with the password are in a directory owned by you and set 700 and the file itself is 600.
If I use just
```

curl -u username ...

```then I'm prompted for the password. I will look at Expect all the same. Thanks.

Edit: I re-read that Q&A about pipes and it's [s]possible[/s] probable that my fears are based on a misunderstanding of what's being said there.

---

### Post by Lars Noodén on 2014-09-29
> **vasa1 said:**
> No, it's about pipes. Here's [an answer to the question: In what order do piped commands run?]("http://unix.stackexchange.com/a/37597") and that gets me concerned over having several pipes.

Thanks.  I'm now going to take a look at [man 7 pipe](http://manpages.ubuntu.com/manpages/trusty/en/man7/pipe.7.html) again.

```

$ grep 1 /dev/zero | head -n 1
grep: memory exhausted

```

---

### Post by vasa1 on 2014-09-29
> **Lars Noodén said:**
> Thanks.  I'm now going to take a look at [man 7 pipe](http://manpages.ubuntu.com/manpages/trusty/en/man7/pipe.7.html) again.

```

$ grep 1 /dev/zero | head -n 1
grep: memory exhausted

```
Your manpage link seems to indicate I shouldn't be worried. I gather that pipes are unidirectional and that if the upstream process hasn't done its job the stuff downstream of the pipe won't be started.

BTW, I don't understand the code you provided.

---

### Post by Lars Noodén on 2014-09-30
> **vasa1 said:**
> BTW, I don't understand the code you provided.

/dev/zero will produce only 0s and never produce the string "1".  So the memory apportioned to grep will fill up before it finds a 1, since it can't, while head sits and waits.  I don't know enough programming to know if that one is solvable or if that is just how things have to be.  I have to assume the latter.  But the short of it is that if you have a *really* huge file and the pattern is not found for too long ( however that might be defined ) then the activity runs out of resources.  I've never encountered it through natural use of grep and pipes, though.  

You can see some parallel aspects of pipes like this: In one terminal, run *grep*.

```

grep 1 /dev/zero | tee a | tee b | tee c

```

Then in the other, while grep is still running, do *ls* on that same directory.  You'll see that a, b, and c have been started even though they are empty.

---

