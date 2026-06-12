---
title: "Getting Fastai.structured to import"
date: 2019-03-24
forum: General Help
---

### Post by Lou Reed on 2019-03-24
In the following paper there is a some code that employs fastai. I will show the link now:

[https://www.analyticsvidhya.com/blog/2018/10/predicting-stock-price-machine-learningnd-deep-learning-techniques-python/](https://www.analyticsvidhya.com/blog/2018/10/predicting-stock-price-machine-learningnd-deep-learning-techniques-python/) 

In it there are some lines that use fastai. The section of python code shows this:

```

#create features
from fastai.structured import  add_datepart
add_datepart(new_data, 'Date')
new_data.drop('Elapsed', axis=1, inplace=True)  #elapsed will be the time stamp
```


Now the line 


from fastai.structured import add_datapart


fails. The code would have worked in January of 2019. The part fastai.structured part has since been moved.

The fastai forum said to try this line in place of above line:


from fastai.tabular import add_datepart


that failed also. I can provide the output when each syntax (fastai.structured and fastai.tabular) is used.

It is just more code, trust me both fail.

I cannot find the answer. Things have changed since January 2019, but I am not sure how.

Anyway, what code will fix this error.

Any help appreciated.

Respectfully,

LR

---

### Post by yczhyou on 2019-04-24
Hi LR, have you found one solution for the problem you post? I would like to learn how to fix this if you have

---

