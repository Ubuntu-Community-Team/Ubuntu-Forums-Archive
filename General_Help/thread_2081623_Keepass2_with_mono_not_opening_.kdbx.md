---
title: "Keepass2 with mono not opening .kdbx"
date: 2012-11-07
forum: General Help
---

### Post by mogliii on 2012-11-07
I was using keepass2 with mono on 12.04. Now I installed 12.10 freshly, and I cannot open my .kdbx file anymore (with keepass2 from ubuntu repository and the standalone version from their website). I get the error message attached.

```
Failed to load the specified file!
Argument cannot be null.
Parameter name: pwKey
```

The same kdbx still works fine on windows, so this is not an issue of the kdbx file. Could this be down to a change in mono? Or am I missing a package?

There is no output on the console when the error box pops up.

---

### Post by mogliii on 2012-11-12
Solved.

The problem were some mono 2.0 packages that I had installed before. So after uninstalling all mono and then reinstalling keepass2 with all its dependencies, everything works as it should.

---

