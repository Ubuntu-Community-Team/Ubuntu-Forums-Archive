---
title: "new user need help , installing cuDNN"
date: 2016-03-12
forum: General Help
---

### Post by yousaf2 on 2016-03-12
I am new to ubuntu while intsalling cuDNN by following this tutorial [https://www.youtube.com/watch?v=6E6Hy3kfEy8](https://www.youtube.com/watch?v=6E6Hy3kfEy8)

 i get this error


cp: cannot create regular file ‘/usr/local/cuda-6.5/include’: No such file or directory


when i enter this command 
 cp cudnn.h /usr/local/cuda-6.5/include

i know may be this is dumb question but i am new so plz help me

---

### Post by steeldriver on 2016-03-12
Well /usr/local/cuda-6.5/include would be a directory that would get created if/when you install cuda-6.5 - did you already do that?

Or perhaps you installed a newer version of the cuda toolkit?

---

