---
title: "curious about bash"
date: 2020-04-25
forum: General Help
---

### Post by Skaperen on 2020-04-25
what is the variable named "-" supposed to mean?  or is this a little bug?
```

#!/bin/bash
echo "'$-'"

```

---

### Post by sisco311 on 2020-04-25
- is a special parameter. It expands to the current option flags. See:
```
man bash | less "+/^ +Special Parameters"
```
and
```
man bash | less "+/^ +- "
```

---

### Post by Skaperen on 2020-04-25
thank you!  now i know why mistyping a #----- as $----- got me some strange output.

---

