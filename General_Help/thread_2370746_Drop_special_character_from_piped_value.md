---
title: "Drop special character from piped value"
date: 2017-09-06
forum: General Help
---

### Post by Superdude_123 on 2017-09-06
I'm trying to drop the character ^M from my piped command, however, I can't seem to get it to drop.

In one terminal window, I am running ```
echo -en "adc read 0\r"  > /dev/ttyACM0
``` which makes my device send back some results with numbers to the same port. To read the returned value, I am in a separate window I am running ```
cat -v < /dev/ttyACM0 | grep -v ">"
``` function that is already cleaning up some of the results, but still allowing ^M to come back. I have tried dropping all but numbers by expanding my cat to ```
cat -v < /dev/ttyACM0 | grep -v ">" | tr -dc '[:alnum:]'
```, but no luck.

I'm open to ideas on how to drop the two characters that I don't want to see.

---

### Post by spjackson on 2017-09-07
Simply
```

cat -v < /dev/ttyACM0 | grep -v ">" | tr -d '\r'

```
will drop the carriage returns. Which other character are you wanting to drop?

---

### Post by Superdude_123 on 2017-09-07
That just got me some blank results. 

If I wanted to filter the character ^ and the letter M out, how could that be done?

---

### Post by steeldriver on 2017-09-07
If you don't want carriage returns to be displayed as ^M, don't add the -v to the cat

```

cat < /dev/ttyACM0 | grep -v ">" | tr -d '\r'

```

If you want to keep the -v for some reason, then you will need to treat ^M as literal characters e.g.

```

cat -v < /dev/ttyACM0 | grep -v ">" | sed 's/\^M$//'

```

---

