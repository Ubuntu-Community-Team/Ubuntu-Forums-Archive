---
title: "To get formula in calc cell to move to the next cell when inserting a cell above."
date: 2017-02-20
forum: General Help
---

### Post by wstay3 on 2017-02-20
Please refer to sreenshot:

If cell a2 contains a formula: = a1. When i insert a cell above cell a2, how can i get the formula in cell a3 =a1 to become =a2 instead of remaining as =a1.

---

### Post by HermanAB on 2017-02-20
Howdy,

You can lock cell references with a $ sign.

A10 will change when you copy a formula, but $A$10 will stay the same.
You can also get more creative with $A10 and A$10.

This is especially useful when you need to make a table of things with essentially the same formula in each cell, but with some references fixed, some partial and some completely changeable.

Some experimentation is required to make it work right of course.

---

### Post by wstay3 on 2017-02-21
What I need is for the formula: =A1 in cell A2 to move down from/as =A1 to =A2 when         inserting a cell in between cell A1 and cell A2.                                                                                                                         That is, after inserting a cell in between cell A1 and cell A2, cell A2 becomes cel A3 and what I need is to have the formula in cell A3 be =A2 instead of staying the same as =A1.

---

### Post by HermanAB on 2017-02-21
Here is your exact answer:
=A$1

Go and play with the $ signs as I said before.

---

### Post by QIII on 2017-02-21
@ wstay3:

Please use the default fonts, do not use table formatting when not necessary and do not shout.

---

### Post by wstay3 on 2017-02-26
> **HermanAB said:**
> Here is your exact answer:
=A$1

What I need is to have the formula in cell A3 to become =A2 after inserting a cell in between cell A1 and cell A2. Using =A$1 make it always stays as =A1. So that could not be the answer. Is there any other sign other than the $ sign to achieve what I want.

---

