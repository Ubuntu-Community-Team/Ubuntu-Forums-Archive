---
title: "MonoDevelop error..."
date: 2008-06-25
forum: General Help
---

### Post by illbashu on 2008-06-25
i am following a beginner tutorial for C and i was useing MonoDevelop and when i went to build/run i keep getting this error...
```

Building Project: first (Debug)

Build failed. Object reference not set to an instance of an object
```
:/

this is what i typed

```

 #include <stdio.h>

int main()
{
  printf( "I am alive!  Beware.\n" );
  getchar();
  return 0;
}
```

---

### Post by iaculallad on 2008-06-25
I don't know what MonoDevelop version are you using. If it's v1.0 then you're probably experiencing a bug (bug # 356092) Try to relate on this [page]("http://www.monodevelop.com/Release_notes_for_MonoDevelop_1.0_Release_Candidate_1") for the bug I had mentioned.

---

### Post by illbashu on 2008-06-25
ya its v1.0 how do i fix that bug?

---

