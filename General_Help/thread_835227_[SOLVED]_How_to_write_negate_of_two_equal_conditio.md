---
title: "[SOLVED] How to write negate of two equal conditions?"
date: 2008-06-20
forum: General Help
---

### Post by abcuser on 2008-06-20
Hi,
I would like to display "Error" if both of the two input conditions are not equal to A.

This code works file:
```

if [[ $1 != "A" || $2 != "A" ]]; then
     echo "Error."
     exit 1
fi

```

But this code doesn't:
```

if ![[ $1 == "A" && $2 == "A" ]]; then
     echo "Error."
     exit 1
fi

```

How to write negate of two equal conditions?

Regards,
Abcuser

---

### Post by Zorael on 2008-06-20
Try encasing the conditions between parantheses.
```
if [[ **!(**$1 == "A" && $2 == "A"**)** ]]; then
     echo "Error."
     exit 1
fi
```

---

