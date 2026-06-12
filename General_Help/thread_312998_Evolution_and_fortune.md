---
title: "Evolution and fortune"
date: 2006-12-05
forum: General Help
---

### Post by Bo Rosén on 2006-12-05
I have a couple of fortune cookie files I want to use for a sig script in Evolution. I really don't know a thing about scripting but managed to cobble together this little thing that works
```

#!/bin/bash
fortune -e b5_quote firefly_quote

```Now, I would like to add a line return and a few dashes above the quote to make it all real pretty like. 
What do I do? Thanks

---

### Post by Bo Rosén on 2006-12-05
Found it on my own just had to narrow my search down a bit. The page [http://evpc.biz/computing/Linux/Evolution_signatures](http://evpc.biz/computing/Linux/Evolution_signatures) has a good example I modified.

```

#!/bin/bash
echo "<div><br>--- </div>"

echo "<pre>"
fortune -e b5_quote firefly_quote
echo "</pre>"

```

---

### Post by moeFinley on 2006-12-05
Cool - nice to learn about the really useful fortune command (sorry if it's a classic, I'm new here) and scripted Evolution signatures! 8)

---

### Post by Bo Rosén on 2006-12-05
Fortune is lots of fun, and you can make your own set of quotes as well. Go forth and have fun.

---

