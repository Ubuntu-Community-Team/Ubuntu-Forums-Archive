---
title: "app or utility  to choose numbers from a defined set randomly"
date: 2015-11-21
forum: General Help
---

### Post by birdy62 on 2015-11-21
Hi , I am looking for an app or utility that will choose numbers from a defined set of four numbers  randomly and then send the result to stdout . The most important thing is to be able to limit the numbers chosen from rather than being forced to use [0-9] only .

Thanks

---

### Post by ags40 on 2015-11-21
My sugestion random.org

---

### Post by raketax on 2015-11-21
You can try shuf -i (range's first number)-(range's last number) -n (number of results you want).
Range is inclusive.

---

### Post by steeldriver on 2015-11-21
You should be able to use 'shuf' to permute the input set and then simply take the last (or first... or mth...)

```

shuf -e 12 34 56 78 | tail -1

```

It can also permute values from a file if you prefer

---

### Post by birdy62 on 2015-11-21
Thanks for all replies 'shuf' will do the job perfectly . I had only come across 'urandom' and 'random' in my search for a solution. I should have mentioned that I was looking for an off-line solution. For anyone looking for an online solution ags40's suggestion of random.org is a good one their tool Random Integer Generator does exactly what I was looking for.

---

