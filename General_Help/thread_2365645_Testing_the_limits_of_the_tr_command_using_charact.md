---
title: "Testing the limits of the tr command using character ranges"
date: 2017-07-08
forum: General Help
---

### Post by John_Patrick_Mason on 2017-07-08
I'm trying to get tr to fail, in order to test its limits. What I don't get is how come I get the output:

```

lowercase letters

```

when typing:

```

echo "lowercase letters" | tr A-Z A-Z

```

instead of:

```

LOWERCaSE LETTERS

```
?

My locale is set to dictionary order aAbBcCdDeEfFgGhHiIjJkKlLmMnNoOpPqQrRsStTuUvVwWxXyYzZ. In principle, the "a" in "lowercase letters" shouldn't be changed, since "a" comes before "A". The thing I don't get is how come the other letters in "lowercase letters" aren't capitalized? Shouldn't they all be capitalized given that they are all located between "A" and "Z" in dictionary order?

---

### Post by John_Patrick_Mason on 2017-07-10
Anybody? 'Would really appreciate the help.

---

### Post by Impavidus on 2017-07-11
I don't use tr very often, but I see you try to translate a range of characters to itself. I would expect that to be a no-op, no matter whether your characters are ascii order or dictionary order.

Anyway, when I run```
echo aAbB | tr A-Z ?
```I get a?b?, so A-Z seems to match capitals only. I didn't check every variable in my environment; it must be the default for my location.

---

### Post by John_Patrick_Mason on 2017-07-11
I see. I guess the reason I originally got confused is because of the Linux command line book I'm reading.

This is what the book has to say about tr:

As we can see, tr operates on standard input, and outputs its results on standard output. tr accepts two arguments: a set of characters to convert from and a corresponding set of characters to convert to. Character sets may be expressed in one of three ways:
1. An enumerated list. For example, ABCDEFGHIJKLMNOPQRSTUVWXYZ
2. A character range. For example, A-Z.** Note that this method is sometimes subject to the same issues as other commands, due to the locale collation order, and thus should be used with caution.**
3. POSIX character classes. For example, [:upper:].

If I go back to page 255, this is what they have to say about commands using dictionary order vs ASCII order:

"
```

ls /usr/sbin/[ABCDEFGHIJKLMNOPQRSTUVWXYZ]*
/usr/sbin/MAKEFLOPPIES
/usr/sbin/NetworkManagerDispatcher
/usr/sbin/NetworkManager
...

```

This command produces the expected result &#8212; a list of only the files whose names begin with an uppercase letter, but:

```

ls /usr/sbin/[A-Z]*
/usr/sbin/biosdecode
/usr/sbin/chat
/usr/sbin/chgpasswd
/usr/sbin/chpasswd
/usr/sbin/chroot
/usr/sbin/cleanup-info
/usr/sbin/complain
/usr/sbin/console-kit-daemon

```

with this command we get an entirely different result (only a partial listing of the results is shown). Why is that? It&#8217;s a long story, but here&#8217;s the short version:

Back when Unix was first developed, it only knew about ASCII characters, and this feature reflects that fact. In ASCII, the first 32 characters (numbers 0-31) are control codes (things like tabs, backspaces, and carriage returns). The next 32 (32-63) contain printable characters, including most punctuation characters and the numerals zero through nine. The next 32 (numbers 64-95) contain the uppercase letters and a few more punctuation symbols. The final 31 (numbers 96-127) contain the lowercase letters and yet more punctuation symbols. Based on this arrangement, systems using ASCII used a collation order that looked like this:
ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz
This differs from proper dictionary order, which is like this:
aAbBcCdDeEfFgGhHiIjJkKlLmMnNoOpPqQrRsStTuUvVwWxXyYzZ
As the popularity of Unix spread beyond the United States, there grew a need to support characters not found in U.S. English. The ASCII table was expanded to use a full eight bits, adding characters numbers 128-255, which accommodated many more languages. To support this ability, the POSIX standards introduced a concept called a locale, which could be adjusted to select the character set needed for a particular location. We can see the language setting of our system using this command:

```

echo $LANG
en_US.UTF-8

```

**With this setting, POSIX compliant applications will use a dictionary collation order rather than ASCII order. This explains the behavior of the commands above. A character range of [A-Z] when interpreted in dictionary order includes all of the alphabetic characters except the lowercase &#8220;a&#8221;, hence our results.**"

My question is, why would the book warn users about using character ranges such as A-Z with the tr command -- because of the collation order -- if A-Z behaves as expected? After all, the ls command uses dictionary order and so doesn't interpret the range A-Z properly.

---

### Post by Impavidus on 2017-07-12
ls doesn't do anything with ascii or dictionay order in those commands. The globbing is handled by the shell and the shell uses dictionary order. Just some experiments:```
$ touch a b c A B C
$ ls
a  A  b  B  c  C
$ echo *
a A b B c C
$ echo [A-Z]
A b B c C
# a is not in range [A-Z], but b and c are
$ echo [a-c]
a A b B c
# C is not in range [a-c], but A and B are
$ echo a A b B c C | tr [A-Z] Q
tr: overtollig argument: ‘B’
Typ 'tr --help' voor meer informatie.
# Error message as this expands to 'echo a A b B c C | tr A b B c C Q'
# The shell expands [A-Z] to a list of file names
$ echo a A b B c C | tr '[A-Z]' Q
a Q b Q c Q
# Now [A-Z] is expanded by tr, not by the shell. It no longer includes lower case letters.
$ echo $LANG
nl_NL.UTF-8

```

---

