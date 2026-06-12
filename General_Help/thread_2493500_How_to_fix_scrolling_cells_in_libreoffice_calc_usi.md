---
title: "How to fix scrolling cells in libreoffice calc using arrows"
date: 2023-12-17
forum: General Help
---

### Post by Claus7 on 2023-12-17
Hello,

I have come across the issue of not being able to go from cell to cell while using arrows in libreoffice calc. This was apparent only when switching to greek keyboard from english one. The solution that applied to my case was this one:
[https://www.reddit.com/r/Ubuntu/comments/zkpuoi/how_to_fix_libreoffice_calc_scrolling_instead_of/](https://www.reddit.com/r/Ubuntu/comments/zkpuoi/how_to_fix_libreoffice_calc_scrolling_instead_of/)

which is that going to dconf editor path:
/org/gnome/desktop/input-sources/xkb-options

and using default value, fixes right away the issue. It took me a lot of time to come across this solution and I post it here, since the majority of solutions mention the scroll lock one, which was not applicable to my case.

Regards!

---

