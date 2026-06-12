---
title: "Zip archive with atool but using custom archive extension?"
date: 2021-07-18
forum: General Help
---

### Post by benyjr on 2021-07-18
Hello, 

I'm creating comic books archives with atool and trying to do it in one command. 

Is it possible to modify this command: 

     apack -e -F .zip dir1 dir2 dir3

to output

     dir1.cbz dir2.cbz dir3.cbz 

instead of 

     dir1.zip dir2.zip dir3.zip

Is this withing atool's capability?

Thank you

---

### Post by Holger_Gehrke on 2021-07-18
'atool' is a script which acts as a unified frontend for many tools which compress or decompress data. By using it you're saving yourself the trouble of learning the various options and switches each of those tools has and it works around several annoyances and 'anti-features' of these tools. The trade-off here is that in a lot of cases you end up with capabilities which are the lowest common denominator for all the tools atool supports. So short of hacking atool to have 'cbz' as a new type of supported file you can't make it do what you want.

You can of course use zip and a bit of scripting to do what you need:
```

for i in 'dir1' 'dir2' 'dir3' ; do zip -rT "$i".cbz "$i"/*;done

```

Or you could add a 'rename' command after the apack:
```

apack -e -F .zip dir1 dir2 dir3;rename 's/zip$/cbz/' *zip

```

Holger

---

