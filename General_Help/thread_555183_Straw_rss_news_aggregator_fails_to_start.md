---
title: "Straw rss news aggregator fails to start"
date: 2007-09-19
forum: General Help
---

### Post by artesian_spring on 2007-09-19
I have version 0.26.dfsg.1-2.1ubuntu1 of the Straw news aggregator. It used to work fine, but now when I try to launch it, it pops up for a minute and then dies (doesn't wreck anything else, though).
When I try to launch it in the terminal I get the following message:

LookupManager.py:31:<module>: No ADNS library found, using synchronous name lookups.
FeedCategoryList.py:377:undump_subscription: exception while undumping subscription: fset() takes exactly 1 argument (2 given)
Traceback (most recent call last):
  File "/usr/bin/straw", line 150, in <module>
    main()
  File "/usr/bin/straw", line 137, in main
    run(options)
  File "/usr/bin/straw", line 120, in run
    app = Application.Application()
  File "/usr/lib/straw/straw/Application.py", line 799, in __init__
    feed_categories.load_data()
  File "/usr/lib/straw/straw/FeedCategoryList.py", line 81, in load_data
    fc.subscription = undump_subscription(sub)
  File "/usr/lib/straw/straw/FeedCategoryList.py", line 375, in undump_subscription
    return OPMLCategorySubscription.undump(dictionary)
  File "/usr/lib/straw/straw/FeedCategoryList.py", line 356, in undump
    sub.password = dictionary.get('password')
TypeError: fset() takes exactly 1 argument (2 given)

Any ideas?

---

### Post by Leandro Lameiro on 2007-09-22
Hi artesian_spring

Thanks for the report. This problem is fixed in straw SVN.

Best regards
Leandro Lameiro

---

### Post by artesian_spring on 2007-09-25
Thanks for the info.

How do I update Straw through SVN; I've never used SVN before.

---

