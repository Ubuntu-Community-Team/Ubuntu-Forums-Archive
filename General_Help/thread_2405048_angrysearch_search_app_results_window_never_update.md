---
title: "angrysearch search app: results window never updates in slow (substring) search mode"
date: 2018-10-31
forum: General Help
---

### Post by rosika on 2018-10-31
Hi,


I run **angrysearch** in 2 virtual machines (xubuntu and bodhi_linux, both 32 bit).
And it works fine* except substring and regex-mode*.


I experience the same issue as the user *jhooly* (see: [https://github.com/DoTheEvo/ANGRYsearch/issues/64](https://github.com/DoTheEvo/ANGRYsearch/issues/64) ) :


> In slow mode, regardless of what i put in the search bar, no results. the results list doesn't change from the pre-search list of folders [...]
Don't even get the results that i do get in fast search.


fwiw Regex mode doesn't seem to work either. the bar goes orange but again no updates in the search results box.


Does anybody know why that is?


Tnx in advance.
Rosika  :confused:


P.S.:
additional info from terminal when running substring-mode:


```
Traceback (most recent call last):
  File "./angrysearch.py", line 91, in run
    self.words_quoted)
TypeError: ThreadDBQuery.db_query_signal[str, list, list].emit(): argument 3 has unexpected type 'NoneType'
Traceback (most recent call last):
  File "./angrysearch.py", line 91, in run
    self.words_quoted)
TypeError: ThreadDBQuery.db_query_signal[str, list, list].emit(): argument 3 has unexpected type 'NoneType'
Traceback (most recent call last):
  File "./angrysearch.py", line 91, in run
    self.words_quoted)
TypeError: ThreadDBQuery.db_query_signal[str, list, list].emit(): argument 3 has unexpected type 'NoneType'
Traceback (most recent call last):
  File "./angrysearch.py", line 91, in run
    self.words_quoted)
TypeError: ThreadDBQuery.db_query_signal[str, list, list].emit(): argument 3 has unexpected type 'NoneType'
Traceback (most recent call last):
  File "./angrysearch.py", line 91, in run
    self.words_quoted)
TypeError: ThreadDBQuery.db_query_signal[str, list, list].emit(): argument 3 has unexpected type 'NoneType'
Traceback (most recent call last):
  File "./angrysearch.py", line 91, in run
    self.words_quoted)
TypeError: ThreadDBQuery.db_query_signal[str, list, list].emit(): argument 3 has unexpected type 'NoneType'

```

---

