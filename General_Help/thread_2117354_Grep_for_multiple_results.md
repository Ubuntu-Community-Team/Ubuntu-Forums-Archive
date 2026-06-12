---
title: "Grep for multiple results"
date: 2013-02-18
forum: General Help
---

### Post by cbillson on 2013-02-18
lets say i was running a command and trying to perform some form of action based on the result, and lets also assume that the only option to me is the test output.

if [ -n "`command | grep 'failed'`" ]
then
else
fi


this will allow me to put tasks into the ' then' section - such as echo to file, use logger, generate email etc.

If i wanted to look for more than one thing however, could i in a single command?

assuming 'command' had outputs of "failed" "completed" "error" "could not connect", are there any other options for filtering this output and performing different actions on each.

I know i've been quite vague, but i'm not quite sure what options are open to me on this one.

Thanks
Chris

---

### Post by evilsoup on 2013-02-18
I would use a case statement.

```

#!/bin/bash

case "$(command)" in
    failed )
        echo "failed"
        ;;
    completed )
        echo "completed"
        ;;
    error )
        echo "error"
        ;;
    could not connect )
        echo "could not connect"
        ;;
    * )
        echo "something strange has happened"
        ;;
esac

exit 0

```Also, with your example, you'd be better off using something like this, avoiding grep entirely:

```

if [ "$(command)" = 'failed' ]
then
else
fi

```

---

### Post by codemaniac on 2013-02-18
Hi cbillson,

You can search for multiple strings using egrep, something like below.

```
egrep "error|failed"
```

You can use grep too but may cost you a few extra keystrokes.

```
grep "error\|failed"
```

regards,

---

### Post by evilsoup on 2013-02-18
grep -E is the same as egrep, so
```

grep -E "error|failed"

```

...will also do that, though I think the OP is simply misusing grep.

---

