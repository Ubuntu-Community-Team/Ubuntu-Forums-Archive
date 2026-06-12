---
title: "Paging and logical memory allocation"
date: 2013-09-18
forum: General Help
---

### Post by forrestgowland on 2013-09-18
My view of memory is that the heap is located in low memory (above the  text and data) and then high up in memory you have the stack.  Is this  how the memory is actually allocated? Or is it contiguous (and paged).  I  know page tables reference consecutive frames, so does this mean the  first n pages are allocated to the heap, text and data; and then you  have m pages allocated to the stack?  For example, if the heap,data,text  require 5.5 inner page table pages to reference them; and the stack  needs 1.5 inner page table pages to reference it, then will there be 8  inner page table pages or 7?  There will be 8 if the stack is indeed  located much higher in virtual memory, but if its actually all located  in one contiguous block of virtual memory then it will require only 7  pages (as the 2 half pages will merge into one).  Hopefully this makes  sense.  I am really keen to get the answer to this question as its been  plaguing me for weeks!  Thanks.

---

### Post by oldos2er on 2013-09-18
Does something like [this]("http://www.tldp.org/LDP/tlk/mm/memory.html") help?

---

