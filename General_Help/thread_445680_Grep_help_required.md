---
title: "Grep help required"
date: 2007-05-16
forum: General Help
---

### Post by crankcaller on 2007-05-16
I've got a list of names and addresses as a plain text file.
They are in the format:

Surname,  First Name
Street
Town
Postcode

Is it possible using grep - or some other program i don't know about yet!  to swap the Surname and First name
around?
I want to do this so i can mail merge the names and addresses for a customer mail drop.

Any ideas?
I've already managed to use grep and find/replace in Open office to clean it up the best i can.  This is the final step but to do it manually would take ages - about 4000 names!

Thanks

---

### Post by ikonia on 2007-05-16
this one is a bit complex because you've got no regular patterns for pattern matching, which is what grep really wants.

What your going to have to do is (I've not worked this out yet, i'll run a test or two) seperate out the top line of the block of the address, use awk to seperate the two firleds then use a mix of sed and awk to swap $1 and $2 around in position.

---

### Post by fanatik on 2007-05-16
something like this will do it:

```
$ cat /tmp/tstfile | awk 'BEGIN {FS=", "} /,/ {print $2", "$1} !/,/ {print}'
First Name, Surname
Street
Town
Postcode
First Name, Surname
Street
Town
Postcode
```

you can then redirect this output to a file if it looks ok for you:

```
$ cat /tmp/tstfile | awk 'BEGIN {FS=", "} /,/ {print $2", "$1} !/,/ {print}' > /tmp/newfile
```

basically it sets the Field Separator to ", " then if the line contains a comma print out fields 2 and 1 reversed, if it doesn't contain a comma, print out the whole line. now if your addresses contain any commas then there will be issues ! but hopefully these will be less than manually changing 4000 lines.

Hope this helps.

James.

---

### Post by crankcaller on 2007-05-17
Brilliant!!

James and Ikonia thanks very much for your time and help.
i'll give this a go later when i get home.

I need to get some Linux/Bash tutorials under my belt.  Not enough time in the day tho.
Thanks again,

Martin

---

