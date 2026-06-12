---
title: "Script problems with Python, Twitter, Oauth, etc."
date: 2016-02-01
forum: General Help
---

### Post by derekcentrico on 2016-02-01
Running Ubuntu 14.04 with Python installed.  I came across a blog post about a script to report slow speeds with Comcast.  [http://pastebin.com/WMEh802V](http://pastebin.com/WMEh802V)

I love this idea.  But, I'm having issues with the code.  I guess my twitter app tokens are in the wrong order.


I'm using Python's Twitter 1.17.1.


Output:
> trying to tweet
Twitter sent status 401 for URL: 1.1/statuses/update.json using parameters: (oauth_consumer_key= ............ )
details: {u'errors': [{u'message': u'Could not authenticate you.', u'code': 32}]}

The documentation doesn't match Twitter App terminology so I used this:
        > TOKEN_KEY="Access token"
        TOKEN="Access token secret"
        CON_SEC="Consumer secret"
        CON_SEC_KEY="Consumer key"



Any help would be appreciated.

---

### Post by derekcentrico on 2016-02-01
LOL.  Newbed it hardcore.  Didn't run twitter at CLI to authorize it.  UGH!

---

