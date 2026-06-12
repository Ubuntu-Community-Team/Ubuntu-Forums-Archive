---
title: "mysql-connector CEXT and Tensorflow 2.1 Conflics on Conda DL"
date: 2020-02-27
forum: General Help
---

### Post by odesseylost on 2020-02-27
I was wondering if anyone has any suggestion on getting mysql-connector-python CEXT and TF2.1 in the same ENV, I've searched around quite a bit and cant find any resources. Every time I try and install the connector Conda wants to downgrade my TF to 1.3 which clearly I'm not going to do. I know it's possible because I have an ENV up on my macbook with both of them, though of course mac is garbage for TF. The clear solution is to just install TF then pip install the mysql-connector, but the pip mysql-connector is written in pure python without C API which for me is incomprehensible. Ultimately I want to thread the data from SQL through the connector with Numpy and Cython to get it to TF, so the C API is important so that the data doesn't hit Python. I'm newish to Ubuntu however and am drawing blanks on how to best do this. Any advice would be greatly appreciated.    With Thanks

---

