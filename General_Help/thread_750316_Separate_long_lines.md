---
title: "Separate long lines"
date: 2008-04-09
forum: General Help
---

### Post by xluryan on 2008-04-09
I have a machine with a really old version of sed. I have a file that is pretty much just 1 VERY, VERY long line, and I need that separated into multiple lines, all with a fixed length.

So basically, just need to insert a newline character every 300 bytes or so. I've tried this:
```

sed 's/(.{300})/\1\n/g'

```

but the box is so old it doesn't know how to read the {300} part. It DOES recognize the '.' as being a wildcard, but just doesn't see the {300} as indicating it's repeating.

Please help! What alternatives do I have??? It should be such a simple command!

---

### Post by bodhi.zazen on 2008-04-09
Not sure exactly what you are wanting but you could try fmt

fmt file > file_formatted

or, if needed, 

fmt -w 50 file > file_formatted_shorter

[http://webtools.live2support.com/linux/fmt.php](http://webtools.live2support.com/linux/fmt.php)

---

### Post by xluryan on 2008-04-09
Yes! It totally was NOT the fmt command, but on that page was a list of similar commands, and fold is the one that is exactly what I needed.

```

fold -w 300 file.txt

```

Thanks dude :)

---

