---
title: "python3 dist-packages json error"
date: 2021-05-20
forum: General Help
---

### Post by powerserg19 on 2021-05-20
I'm hitting unresolved json attribute issues while trying to either reinstall software packages or
 more specifically running dejavu back up tool. The common error is module 'json' has not attribute....
I am running with  VERSION="20.04.2 LTS (Focal Fossa)


I have tried several things to restore python3 but to no avail.

[B]Example 1

[/B]
```

{11:40}/usr/bin &#10157; sudo apt-get install --reinstall python
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Note, selecting 'python-is-python2' instead of 'python'
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 2,496 B of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu focal/universe amd64 python-is-python2 all 2.7.17-4 [2,496 B]
Fetched 2,496 B in 0s (37.2 kB/s)            
(Reading database ... 274355 files and directories currently installed.)
Preparing to unpack .../python-is-python2_2.7.17-4_all.deb ...
Unpacking python-is-python2 (2.7.17-4) over (2.7.17-4) ...
Setting up ubuntu-advantage-tools (27.0.2~20.04.1) ...
Traceback (most recent call last):
  File "<string>", line 2, in <module>
  File "/usr/lib/python3/dist-packages/uaclient/entitlements/__init__.py", line 1, in <module>
    from uaclient.entitlements.base import UAEntitlement  # noqa: F401
  File "/usr/lib/python3/dist-packages/uaclient/entitlements/base.py", line 16, in <module>
    from uaclient import config
  File "/usr/lib/python3/dist-packages/uaclient/config.py", line 12, in <module>
    from uaclient import status, util
  File "/usr/lib/python3/dist-packages/uaclient/util.py", line 102, in <module>
    class DatetimeAwareJSONEncoder(json.JSONEncoder):
AttributeError: module 'json' has no attribute 'JSONEncoder'
dpkg: error processing package ubuntu-advantage-tools (--configure):
 installed ubuntu-advantage-tools package post-installation script subprocess returned error exit status 1
Setting up python-is-python2 (2.7.17-4) ...
Errors were encountered while processing:
 ubuntu-advantage-tools

```


[B]Example 2 Here is the result when Dejavu back up tool runs

[/B]
```

Traceback (innermost last):
  File "/usr/bin/duplicity", line 106, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 92, in with_tempdir
    fn()
  File "/usr/lib/python3/dist-packages/duplicity/dup_main.py", line 1525, in main
    action = commandline.ProcessCommandLine(sys.argv[1:])
  File "/usr/lib/python3/dist-packages/duplicity/commandline.py", line 1175, in ProcessCommandLine
    globals.backend = backend.get_backend(args[0])
  File "/usr/lib/python3/dist-packages/duplicity/backend.py", line 225, in get_backend
    obj = get_backend_object(url_string)
  File "/usr/lib/python3/dist-packages/duplicity/backend.py", line 211, in get_backend_object
    return factory(pu)
  File "/usr/lib/python3/dist-packages/duplicity/backends/pydrivebackend.py", line 72, in __init__
    gauth.CommandLineAuth()
  File "/usr/lib/python3/dist-packages/pydrive/auth.py", line 111, in _decorated
    self.LoadCredentials()
  File "/usr/lib/python3/dist-packages/pydrive/auth.py", line 289, in LoadCredentials
    self.LoadCredentialsFile()
  File "/usr/lib/python3/dist-packages/pydrive/auth.py", line 308, in LoadCredentialsFile
    self.credentials = storage.get()
  File "/usr/lib/python3/dist-packages/oauth2client/client.py", line 407, in get
    return self.locked_get()
  File "/usr/lib/python3/dist-packages/oauth2client/file.py", line 54, in locked_get
    credentials = client.Credentials.new_from_json(content)
  File "/usr/lib/python3/dist-packages/oauth2client/client.py", line 299, in new_from_json
    data = json.loads(json_data_as_unicode)
 AttributeError: module 'json' has no attribute 'loads'

```


Thanks Ahead of time!

---

### Post by dragonfly41 on 2021-05-20
Without looking deeply you appear to be mixing python and python2 and python3.
Do you have conda installed to create python3 env?

---

### Post by powerserg19 on 2021-05-20
If  I am mixed it and if i did it, it wasn't deliberate.

I am not familiar with Conda. Why would I want to crate a python3 env? 

Thanks

in /usrt/bin I have this

> lrwxrwxrwx 1 root root      16 Mar 13  2020 python3-config -> python3.8-config
lrwxrwxrwx 1 root root       9 Mar 13  2020 python3 -> python3.8
lrwxrwxrwx 1 root root       9 Mar 13  2020 python2 -> python2.7
-rw-r--r-- 1 root root   23560 Mar 13  2020 python3-minimal_3.8.2-0ubuntu2_amd64.deb
-rwxr-xr-x 1 root root     388 Mar 27  2020 python3-pasteurize
-rwxr-xr-x 1 root root     384 Mar 27  2020 python3-futurize
lrwxrwxrwx 1 root root       7 Apr 15  2020 python -> python2
-rwxr-xr-x 1 root root 5791744 Oct 20  2020 python3.9
lrwxrwxrwx 1 root root      33 Jan 27 10:41 python3.8-config -> x86_64-linux-gnu-python3.8-config
-rwxr-xr-x 1 root root 5486384 Jan 27 10:41 python3.8
-rwxr-xr-x 1 root root 3674216 Mar  8 08:02 python2.7




---

### Post by dragonfly41 on 2021-05-20
[COLOR=#000000][FONT=&quot] AttributeError: module 'json' has no attribute 'loads'

[/FONT][/COLOR]Just a thought .. do you have some file named json.xxx which might cause load conflicts

tip from here ... [https://www.pythonanywhere.com/forums/topic/13275/](https://www.pythonanywhere.com/forums/topic/13275/)

---

### Post by powerserg19 on 2021-05-21
Very interesting... 
In /usr/lib/ I have 4 different versions of python
```
drwxr-xr-x  26 root root  24576 Mar 13 09:59 python2.7
drwxr-xr-x   3 root root   4096 Jul 31  2020 python3
drwxr-xr-x  32 root root  20480 May 19 07:37 python3.8
drwxr-xr-x  30 root root  20480 May 19 07:38 python3.9

```

I moved  python3,8 and python 3.9 out of there 
and when I ran the Dejavu back up tool it simply failed with "unknown error" instead of the json error



[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAYAAAAD5CAIAAACh/3VVAAAgAElEQVR4Ae2diVsUd57/5w YZzJJZpNsfnNsZmY3 T2zu5OZnf3ts7NPF13dzY0iyiEeIIpBjEajeMR4gJySeIACggIjgiQoHtgoCsh9KALSiCCXQcQYRQ67uyrGOPt7qrurqL6gqy3k8N2Pj1RX1 d7vKq L75HVfOTXrxAAARA4KUT6OvrCw0N/clLzxcZggAITEygtqV XuKitzf /qdr3525/97e Pt5Cf7lTZXmFe7r6wsODoaAzMlgDwhMMYE6Vf3PNv7qtS9/OM91/P/mDm/vt5xvuvxb/3s42/qlPVmzC9c dOUFAQBGSCBW9BYOoJeCUufi3 vZnrHZOSvxb/3vyDi82xLlu2DAIyx4I9IDDFBN7a LvXM2d234fvoJ9nvP/Oxn82ZxoYGAgBmWPBHhCYYgI/XfsuvwHPgu2frn3XnGlAQAAEZI4Fe0Bgigm8IgJaunQpBDTFlxqyBwFzAq IgJYsWQIBmZ997AGBKSbwigho8eLFENAUX2rIHgTMCbwiAvJfuBACMj/72AMCU0zgFRHQn377Rwhoii 1mZR9z/ULGYl7ImJzarpnUrFnYFlFFlAOubTtQmadyy m7p5Gi6tgv3vzPQhoBl6eU1XkzvytToTEYUH0pa6pKsIrkq/YAvLeN/K0vXX P0wzAX347r9DQLP9ku65emzz4vlzXBxJKeFAKly9FoVs2ZtX025HvW0RkP4YwnHzyU5DDp0FOzwIiUT2aW6HHXm miF2C iNr9wDVAU1o4/Uz3/8/ocHt749F33F4c2caSqgv/7mvyCg2X6Fd1fuWyyVSAjSyX3OXA8XuZSQSCSER1huc4/QqkNAQonZe7x9Anojb m QfWPP3QVtEWHVKxeUr0zsuPCocr/eQMCsvdEIO6FCRgERK5K1xmn8/rxT90ICeEYlqfrkNxSfrFyoaerIyklneb4r959vJLtG/W0lmZErPaf40hK5W4 IfuLOvgC6qxOC2XScVp oPQWr5Dj94C6KtK3rgrwmeuiIKUy53lL18UcL28TLEJedrN00y4BfejW/s2zH5qiL/zZ9M5pEwHlEPNuFDZq1N8/f3J3UBlRImHnhv6DqD9Zpx79/u8/qKmuk7XyN/VDthMyP9XFhidD2h9Hv3mYv/Hif74hfChncQ7or79GD2iWXsFj1TISUHdHc8nBVc7MRE7MZd1ETteFiPlO7p7zF3i5KxwICSFd EUp80F78ZcBCkIiIRzkLu6uCtnSA1XdnICKmgt2L5QRBLlg28kmY3 MLyDDp4TcZc4cVznBpO 8MqUKU0pj50u3ZY Avlp14vsfv 0KftfcDkYC lDR2k7/0J7dsHpu8cdbejrUz9r2XPzj69kf/EKZqHr 8FLzKsfC c5XNvqc/3edyP7kequb0lbEVS4mi1ZH3Pv2qfakz9eCH9CHgExO8Svz1iAgCe9FkN47z6gM4ujp7u7p6lA1NVwrS1mlICRkcMq1np6mjNWOhIRwX3ukqr2nt7frVltHT69BQHNDNwa7EoTDnLVHq9mJHg6nLQLST2P3tF7as1RGSAiPz89idogDqNuwQ0C/OPdFw/OnV r/x0L3hCegN/I Pff06fUmN0OvJ8c9cvDp8DfrfpP9wVvFOQPPuxMv/YnfgXojb9P5H54oa/5bn ybp6Oqnw9lX9G7SYCGICDjM/zqvGPngJy9A5cvXx64yMtZynR05qw7drWnt7f7 pm4VV4Kpi9ieEmXMH2d05 5MP7Zfo5vGL1c9McRrhtPtBh3fnRMbRdQb2/P9bSVpEQiXby/Euv6RlekPQIq OL686el9X8dX0BvFR3tft53sOhfWcv8q0v73aejR2Q5H7yeO3fLwHdPn/VXdu1dVvhX/ZLZW0XpPX9//uz50 8N/579 L9PS os5WLe8 LtsSig/8YQzOi0z8o3RkOw3t7enrZzO7wcJBJpQGJ1d9vJzcxEjktQRGr2iWMxwY6ERLrkQGV3Z/4WJ6ZvsqPAXECEk c8xk5Sr025183E0Vmww52QSMiP/8bq6VbuBqYz5bT5VCfbhzIs5Pc0Z4QyAlq0txyDMKOLzw4Bvf7VmlNPf y/HfgOr9kbLMPrATFCsSYgJvDP/1EakTzQp/n7cF2z9z9mf/BWUUbP8we51XP X4Eb 8/lD1//gfWXrZ0gCMjoBL9Cb0wE1NNRl7meWRaXBh6s7aw7tEwqkZCrjjIzOfr1cp2AuuuSgkhC4jB34/GrtxlYnW1tHT2GIdiCqHMX9iyVM1JZmVzFNxTjt4a0lcy4Sh4Qc 5qW0db3Zm4IMZl5LJDtd2sgLx2X js7e26lrGGMZnTxq/aXqETYktV7RFQ9n/693z37Gn15gKz8ZFOQB2tC/4h 4M38jYU/PD0epMrNwTbPfh05Jv1vzHS1p9dbnU/pXLnnfjgjZNbLjx71qqa97bRAbZ6h/MUBGTLeZ Nx7BDMNJlrpeXp4cTqRtuES6r0 u7ezuUuzwdJATh6BUQEhq6dC5p6AH19jTnbfFkVuyZSWgPdyeZYm1W6 2xGxE7q5KY7hLhuPxgpbGCelRndszXrfWzgzqJhJDO25rHLMIZBnEEQTrP8XRjZqEJqffuQv4y2mw8B4LrZJeAPnjz9Pqv1T88o29k3/g84MqKBWUbNrRkJ1Y7vpmj2PbwB 2jI37n/vJG9oeOukno49dC5xSv3tLdoX52K/7ih8wk9NlVYXWr3S96kZdWRw08ejqc7JDzwevZf5nb3vP9s95zNzb7Fi dV7Z5a 3CXwuXEQQk CKYJQE9VzM3Lpyj8w5BOJCObvOXhG47kFejb/Q9rcWp21Z4u8qlBCGVOXl4B4RG5TXq5nZu1 fvDQta4CaXOpDOnku35VzjCai3t6vyYJCC6b EHr1mMhfU1VCQuHWlrweztu/o4btya8KZa3pLGWaIFPP8vN3kpNzNNzTyRI2uizVLaItUDfsExEjk1KKNHVeaNSPU8x /f/b4zmBZWo37W9n/919K0yrVI7fbFr6V/cHrOQ5eNy40adXfP1f3DxbuZpfh37m0v3z0MfX35z/ ONzz8PQmbrn9hNT7hrJBPUL//Uf6 /7rnZ/ gRGTsH8QkEiXBpJ5EQLsIA4Pc4xP0W4BCfXCSzveooDI//hjuhx78S8KmoBCAg23C IgL67Rv/BAHZdkXgKFEIQEC2YXxFBPThe/g6DtsuCBwFAi TwCsiIF9fX/SAXuZ1hbxAwCYCr4iAFuIbEW26HHAQCLxcAhDQy WN3EAABHgEICAeDGyCAAi8XAIQ0MvljdxAAAR4BN7e PtZ9qeZ37b0p5kxB8Q759gEgWlDwDNh4Wvx7720uwQnO6PX4t/zTPA3pwsBmTPBHhCYegKX60t tvGXr8W/9/OM9yfbDpOa/s8z3n8t/r2fbfxl8dVSc6wQkDkT7AGBqSfQ3d1dfq3CK3HR2xv/ adr3525/94J xfPBP9LdcU9PSYPDDKQIaCpv9RQAhCwSKCnp6e9vf3mzH 1t7dbtA8EZPG8YycIgMBLIoAe0EsCjWxAAATMCUBA5kywBwRA4CURgIBeEmhkAwIgYE4AAjJngj0gAAIviQAjoMt4gQAIgMBUEHB1df0JjRcIgAAITAWBoKAgCGgqwCNPEAABmoaAcBWAAAhMGQEIaMrQI2MQAAEICNcACIDAlBGAgKYMPTIGARCAgHANgAAITBkBCGjK0CNjEAABCAjXAAiAwJQRgICmDD0yBgEQgIBwDYAACEwZAQhoytAjYxAAAQgI1wAIvLoEBgcHGxsblUrlsWPHEhISYmNjd tesbGxCQkJx44dUyqVTU1Ng4ODk8QIApoksEgWBKYvgeHh4aqqqsOHD4fb/Dp8 HB1dfXw8LC4tYKAxOWJ1EBgWhN4 PChUqmMjo622TxGB0ZHRyuVykePHolVSQhILJJIBwSmNQGtVltWVmainsjIyIyMjNLSUpVKde/evZGREa1Wq9FoRkZG vv7VSpVSUlJRkZGZGQk30PR0dHl5eVarfbFKwwBvThDpAAC053AwMBAcnIyXyIpKSn19fUjIyO2FH1kZKSuri4lJYWfQnJy8sDAgC3h4xwDAY0DBx BwGwg0NLSEhMTw7kjJSXl1q1b9lWsra2NL7KYmBiVSmVfUvooCOhF6CEWBKY7gdra2oiICL19oqKiqqqqKIp6kUJrtdqqqqqoqCh9mhEREXV1dXYnCAHZjQ6BIDDdCdTW1nIdn8TExLt374pV4r6 voSEBC5xux0EAYl1RpAOCEwvAi0tLVzfJzU1VfQV9KGhodTUVK4fZN9YDAKaXhcNSgMCohAYGBjg5n1SU1NHR0dFSdYkkdHRUc5BMTEx9 /fNzlgwrcQ0ISIcAAIzDACGo2GmypOTEwUve/DxzE0NMSNxZKTk4WuzUNAfJjYBoHZQKCsrEw/MoqKiurr65vsKt29e5ebk66oqBCU3fQWEDXyoPfmtfKLRY0DLzRxLwjJdDpYMzTQ1VJff u7Sao Nfpw4OGkdM6nE8VXqyyPHj3i7jasqqqyWHmVSmXHWhhFUdYmeqqqqvTKi4mJEfTg2PQVkEaVFuTkQEgkEomDX2Kj2iLIWbGTGmrN27Xc09nZKzjyzC3DjWGaW9nrfVxlBDEZ1dd2nY/f/HGQ3xxHqdQ/6YZmVmBEJfQElEql3gUpKSkWLVNcXBweHp6fn2/xU2sYKYo6d 5ceHj4xYsXzY hKIob9BUWFpofYG3P9BWQuvGAnwOjn8logdZwTMV bWdmMKkTrURCyD/O/UbX25nU6qvr470MOUJAU3HOJy3P4eFhrvtj8W5DlUql11N4ePjp06dtdBBFUadPn YCLfaDbt68qT8gOjra9lknKwLSdBTs3RG2ZmWg/wJPNycFKSUcSLmTq6dvwEfrtscfOVPbOzxJgwLu1ExqC RyEbzxpCzCxdB29XY0/59cld0rgI66/gsvg2klEoeFiU26zt6kVh8CEnzeZ0hAdXU11/2xWGQTldjiIBtD J2g6upqi7mb77QioImaGUF6rTt69YGAZmae9QR7JrUFTpD3OB9PREYikQgUEDVYtcdH3wUiSP/9V/XfdzCp1YeAxjnDM/oj7hs26uvrrVXERqHowwUdXFdXp9dfamqqtdxN9tspIObXPuG2IV8/XDBJU5y3k9oC7S i AKiaVpzv/H83w4fziq88YB9wHhSqw8B2X8BTOPIwcFBffuPjIwc/ylTG7Vi42EckpGREe65 cePH3P7x9mYWECE55a/FZeXl5dfKSk6eyIlIniOlB2CSAMO35y0CcxJbYHjEJngI56ACFlw3FcnzV/5pW1DL9w3nNTqQ0ATnOWZ XFjY6NeQJmZmRPWgJtU1oeYz0lPeIDFLNLT0/UJNjc3WzzAZOfEAuJmJQyRwzV7FhimLAjFtiLuaX7qu6YzybHb1gUv8fZwVpAODqSTh3fgmp0H8xvuWV7CGu6pzNm7NcTf01kmlcqcPHyCPo1KyW8wrLhbboHU/dJIH9aAhHPIkRtD9FDhFrlhJoZc83U/2/aflEe6GVRJBqW3G7oW1OOO8lPpCTGfb1gV5D9/jqsjKZXKnT39V4bFZhTd/I7tgJhgGnvLF5DTzpInY5 YbtkMxGJNLe7kZaH59kZBSvjaAC9XBSl38vAOWr87rbDVcvlHesqz4jcF 81xlpMyF6/ATyO3r3TFJDSP5uzY5Na/SktLbanROB2ccT4aP2X9Elt4eLhSqRz/SP2nwgWkbk70l rbO EeWc61QGrg5DqZ YysREI4eKzNajX JkdqqPXrbX4Ktis1FkYuO2pQhaUW KTjxCesVAipd/glnW0ECYiX7Fiuhi1COic0qXr8W44ECMhWILwijd1wYHGn4YxS39alrPbQ36LArwRBeoXlqIx7X9T9yn1BTuag2TisgtnSTGbGMceOHdP3PiyuUlmsg8VujslOWyaqucS5VbasrCxu5zgbNgjI98uqgQcPHjz49t6djsbS3KggZ8Pl7DA/ppL3XdXqOm5tl7262Z EbHkG2wWhaVrbe3bTXIttwsF7X4Ohu2TWAqkHlfGLZIYwwjU0s9XQ xJNQExxCaeVR1u4bp05OdsFRNsKxKymTK4Wd qKo 7IWcP2X1jA3E/CYUFU2dhti1Tf2U0eFkmzERCQ TmeqXsOHDigF9C9e/dsr4N5Z4e/4i7IPjRN9/f368uQkJBgSxkmFhB7pRr/JKSen2Q0PmKHO0xW1EBZ v603LNFJRU11xquVRXlxAZzDYVcntHBDoIGlFvd2UZBkJ4hUUfylEWXL549kRofnl7PNn6TFjjUfmIdG0XIFsWVj3VU7BUQ4fFpSsGlktLL545/ cl8Vm0SwnFNrvVldJ6AjIkY3hHz4usMCrUViElN9dEWdzKU 8 GGagSDnNC9 WXX7/RVFOYtsnHUAGCDM7sNKBWX fupZIQpPeGgycvlZddOpudsNGPrS4EZEszmRnHxMXF6Ru/7bfh6Ctm0uXRJyLoRiEO0NDQkD58z5493M5xNuwWkMvS7RlVfZYnd9j8qP68TwzDLMJ5V6l tEb1HA9hr37CfcPJbitp8Fugz67EcD/DzXqE1Ouzsz38IHsFNDbeoWlNb/5GdnAn4dmSrQr3U4CAuBhuwyIQy50dfvV5N4Jrb2euIPWuI buKhn7DTDayI2MydVjNzP6stN15PIjbRw0TEJzp2Q2bXArUBqN4LUhcwcJ7fvoSWo0Gr2AIiMjbWFrr4CYNkBI52 /wM356nIbuaeqUOYdT085sPfLfYmpmV sZvtA8k3ndcM16rtzYezcj4PPvgZuDsm0tLwWSDAvXasjHOZuyG1jO0mGEDEERNOjtfHs/YCEIqzgIb9zxyubQAFNDMTKaItXfZ4oqQdnN8gNvUcHz5Xbdo29doRyawOee2oZ11D38tYaZCUhgzO7xibYISDeGZ09m IKyHxdzBZS4gtobBWMUg896G4sOsL19pmHJBLYp7TUd0r2h3qyzxQYBiRjP2RhBbpf15q2tEDDHLZEvum89T/vwWuBY6kQTsEp18d 7euJiCMg6tv89ewk jhdIJ6ALC7DnzrfYHCyjUAECYhPb4yKyRbhpO9tatpSAzjUWy8MjV0/ENAYi1m0JfoQzA4HiT8EGxMQe6pGquPYvgIzWrnN/GYdaUoKZH81m7QH/VtOQDd5rWKz0vrNSjwBjfWAmH6Xx4avbxv1m/gCWp3bx3ZdLC/D85Ll9SyYqj0qCOMEFJTOzlixlWZ/8gU03jK8zUCECejmYc4pFjEzOwmPqEqmB6ThoWbx66sBAbGnc1b9nJ2T0OYC0j09abj8DZ OlO3mZojd16RW3L4/pNaoRx6U7PY0DBjYFkDdO/kJ286li8Z5EptvCt/orKQQdjAnIeSBBxt4v8 flO5i15mlS8dujRQoIG370WXsgEW2Pv8 6zGTS9RGAdkOxAYB ey/bpi oe7lcfTIlcd4oyqTYjJv TdGOHjvu8ZNAdEQkAVcM3/Xiy/D6 d9TOaDBPWDWlpa9HNA4i3Ds49HsidI3Xl8tSO7ikWGMA9eUn25H7NTo4ptl7g5Gt6FzgqI1jQfZO8jkjjMjyi21tL5AmJmYR9Uxi1kB3iE1CfqyresIjQ3DrEpEvI1X7FdIGECGlWlBLLJmzuXrTtN2yYgIUAsT0LzMBHO2y6ytzvw6ipx8N5VdHe82UaNKnkJOwYjPLac62NngXjnBatgY d2pm9xNyKWlJTYUhfzBXju4fhxPho/ZfFvRCQ8t2SVVdfU1NRUll7Iz9z/WaA7dwscQQaktmlomnp0fhM3szxv84nrfY/VjB5GqmPnmfSAaFrdmrKUbeoSQuGzPj7zVOGly5cvnM09ui8isYidQjH7Oo7hG4eXs7lICM/PL9wzKGioeCe3gkW4BcccV5ZcKb1csD E9STvTmie1wiF/5ak3PPF5eWX8hLXzefKxJvYModto4AEATGrKXOvVNexlWyHjCB9t6RfvNozSNG0pu1IEFdSQuqxYseh7LMXL18qPPNV1pHEqLDgrV/1sGamtR2ZwdzAmJB7r9 fc774ypViZRJ3JxEEZH6OZ qepqYmfe8jIyNjwjqYdHPM17xMDrCxH3T06FF9GUR7FMPqVIOEIH2iy/RPxFN3ctdwbrAYwfWAaJp6WBnHLqqbHkt4xtbohwo8U3CTNU/a0ldy2RCeO4oM3afh i99OSuaJsk8nz72KAYvWQsHMjMo7mFnxnnG1jYB0UKA8IrE1ZSmn9TFz e pUMikbAP3lGDdfsWs/cxmFeB8IjWTQAZLsChhsQATkHmR0skENCETXXGHDDlD6MODw9zK3GiPYxq6arVPV8RHF/UPTYZPHIz xMLTwdw0TwB0TQ92nU cgk7ccMdw2yQoSfG 0auJzePruAU5OAdV8X0CpguWH1SsPXv6bFZQITTsr0VY7c4Wrj0bBQQTdsOxLKAaO2dgq1e7GNvEsJxWxE776XuvbQnyMVwZ4IRPT5AQ E135R8udzVysEQkIVTPJN3cV/HMc4f6hI0vBJ0MPdnyNLS0mykaOU IE3bqd2fBPnOdVFI2UuXIBxIR9d5fkEfb41NOVlx23QxnKbV9xpOJ 1aF Q711lOEszxCpc5C/yDPt4U/uXhE5VGNw8yEuqrP3Vw19pAbw9HkiCYJ0L9gtbtPHCyUd pstIs6ZHGg0vYMQghCzrK3V430luZHb8peOFcJ9KBydvJ3WvhslWfbo89dOxsTQ87L8VLlvBYtXP3uqXznGVS5sHZoLC4rLJu9jhr/GwWEPM4hW1AeEXi9YCYAqj7r bt/yxksZerQh6QavTNA qBxnOHIzes8JvrLHMgpApnDy//oDWfxaacrObqytVBf/Cny33nOOlQO7l5 gV8tG5bdEJGfkWn8cNjXBA2ZiCBafKFZDU1NTbCsyIgG6Nn4GHWW/sMrAyKDALGBPhfydrW1mb8IfOOe1hU0JMWJv0giw 7tra26md/xPhKVvOCz5Y9ENBsOZOoh2UC3FpYUlKSxb/SVV5e/iJfSm9xiU2r1c62L6W3TPeF90JAL4wQCUxrAlPyZ3kqKir03Z/Z82d5JukkQ0CTBBbJTh8C j5OeHj4y/nDhH19fdwfJqysrBTEAXNAgnDhYBCYAQT4A6KEhIShIXb9dBLKPjQ0xD0CkpKSYnHQN062r5yAxmGBj0Bg1hAYGBiIiYnRD4tSU1NHRyfl79 Ojo5yC/ xsbH3798XCtA/IOgnQmNwPAiAwPQnoFKpIiIiOAeJ3g8aGhri7BMREWFxaWxCSg6 ENCEkHAACMxMAtwf6goPD09ISOjr6xOrHn19fdzIKzw8fJw/QzZ jhDQ HzwKQjMbAJ1dXVcPygqKqqqqkroNI1J/bVabWVlJTfrHBERYbd9aJp 5513MAQzIYy3IDCrCKhUKm4 KDw8PDk5 ebNm9yD77ZXlaKo1tbWpKQk/bAuPDw8NjbWvpEXl mvf/s7CIijgQ0QmJ0E7t /z90oqNdHcnJyXV3d H9AlWMxPDxcW1trkkJKSoods85cmvoNDMFMgOAtCMxOAlqttqKigt8VCg8Pj4yMTE9PLykpUalU/f39w8PDGt1reHj47t27LS0txcXFR48e5Z5x18srJiamsrLyBYdyesoQ0Oy82lArELBIYHBwUKlURkdHc8MoQRvR0dGFhYWDg wX5FnMQ8hOwgerYEJ44VgQmAUEhoeHq6urU1NTbbdPWlpaTU2N0L84NiGrP7kuxRzQhJRwAAjMTgKPHz9ubm5WKpVZWVmJiYlxcXGRuldcXFxiYmJWVpZSqWxubrbx28XsYPTOu7 CgOzghhAQAAERCPz6/7wLAYnAEUmAAAjYQQDPgtkBDSEgAALiEICAxOGIVEAABOwgAAHZAQ0hIAAC4hCAgMThiFRAAATsIAAB2QENISAAAuIQgIDE4YhUQAAE7CAAAdkBDSEgAALiEICAxOGIVEAABOwgAAHZAQ0hIAAC4hB4/71f4k5ocVAiFRAAAaEE/iJzh4CEQsPxIAAC4hDAEEwcjkgFBEDADgIQkB3QEAICICAOAQhIHI5IBQRAwA4CEJAd0BACAiAgDoG/yDEJLQ5JpAICICCYwPv/hGV4wdAQAAIgIA4BDMHE4YhUQAAE7CAAAdkBDSEgAALiEICAxOGIVEAABOwgAAHZAQ0hIAAC4hCAgMThiFRAAATsIAAB2QENISAAAuIQgIDE4YhUQAAE7CAgqoCovpJD2 POdmltLwh1ry43KatygLI9ZMIjqQcNeYfSLvcKKMaEadp3ANVffCBs19cdU18S 8qPKBCYZAIvLCB1Y3KAx6ID9SM0TWtakhbLlqS0amwvtPr6fh958N EOIumaX6m1NCdxvKajsdjCtPeOrJM7p90Q0AxbC woCOnT0kEFRsHg8DLImBJQNT9/PUyidFLtuHMg7EWzi ctiNv26otOTfVL1NA/EzVdfHzZCHHe8aKN32a/fQpCf UYRsEpg0BqwIiV6fVNHCvxo77NvQnXloPiI8PAuLTwDYIzCgCVgUk31I4ZFQTbdepzxbNdZJJSSfPgE0plf36iQ3 L3kTAam/KU/7/CM/D0eFq09oVF7LoKGTMtpVlLBhyRwFqfDwX/NJoKvMeAg2Wh3rSQYcvqk33pOqmLnyNXn9uljqwdkwhfO2ooe8QRYjIILtrsm3FY3QTJFIx/n fh4KUu7q/VH4iaZHY/0jplJW6kL1X967LsjP00UulVoMNJYddScnVO4VX6 mrQXy4FCDDUnLnTzDTnWpaavHM0W7V5OxI3iBs0zm4h28M7NuQEvbAOTRRCVnxq2WTgc1UHn4s5BFns4yknResL3gHmW x3KpdBeHxYONLhu8AYHxCIwjIOUjjeGl1VI0TQ3eqiqtaWxpuV56bIs36U5oFjAAAAp4SURBVLHzsq5V89qY8RzQcEPiEoXXhrTLDaqmK5mb5pNeMZWPmWSq4/1Il6CY3JKa2vKCI5/5K0hjAdGPLm5zVnyaf5 RhqYtNUBKuEVcYeaY6NGqmLmKT/L6NSYCki1LrGxrb29v77j7mNILyGNdSmF5bX3F2YTVHlKvmEojm45TF9m8LVnltfU1V/L3rXI3DbQmIAaCpUAWjvpJ56kwT5fglOt6CVs7nh5pTg5UOC2L upKfX1pbmSgkyIo9caobUAsFWDs1Fs5HUxJSM wzNK6hmvVV65/o9XTM9pjpVRM2ubhYzliCwQmJmBVQGyfgvkpXZzUwh BaTvSl8v9EpuYeR 2jTGf83pA1MPCrc4uW5SGmSPqbu7HMo oiifUg4JNTvLQnF5Dl8TSJDR17 Q6hduu0iGapu5 tcbJ1c3Z78B1NU1rbiQtkq/I7NTyMzWWAlNj/qc0rWlNWUIu2HuVKayFl7W60LRGlWwaaJzXWA/IJEcuUL8/8fKF3X5Oi2PLuLU K8dTj4q2ucpW/q3TsGqm6chYIXPdfvmRICCWSm7tdJiwYvgYl42maWulGrR0sAXC2AUC1glYFRC5Jr2hxfBSdfSP0E96S1M D1nk5e7iNs/H00k6/8v6cQSkbkr0cyCkpIx9kQ4EM5P9pDHBj1yY2Mz6zJKAaKo3Z5V8/hf1T5h24/FJ rHNrkHp7Vptd9ZHiqXM2IzfSIylwNSU/ylNUw/PbZQ77ix5woNgQ11omvrurGmgcV7WBDQWyJSEVLi6yMiAFBXPgCYlZDNSNyUuJA1i15VWfX2/L l/6IZaCBBLJbd2OijjkpjTY4Zu1kqlMUXNI4xNELCJgFUBmcwBadszVihcVu49V9vS3q4q/nIpOYGAGNF47S5s7xx7dfUPapmWQPolNrKt0aKAaO3tzBXyhYmNj0rDPUOyuu6eXOccmtPzzddrHP0P3lAbX/fqunivcVfBBpWb5Yrtl8cEZFNdaJo2C6TV9V/OlwVnGnoo1gQ0Fsg0b9mCsJgtvnKX4JQGbibKpNmzGRng6HqWurPHCkgjBIilkqutnA4TWTOZmpRNJyDmlFkolYWDbbrocBAIsARsFdDwha1yWdi5h/q54L7c1XKrAkpWaWiaelCw2YkMTGtjTWPIkHp0cZsLGXSE3W9ZQLS2M3OF3P/L1HCvwMM3NVRv9irnj5OS1zotOsT4x6iRMG3L OYjkybENm 2yrRNdbHUjGltR3oQOWd3 bAuLdsExNyRNHKncLs3OTcsv1uPw0oJdXBkK7m7ojQdmcEy1 2XBmkhQCyV3NrpMCKpB2RSNmYIdnGbi VSWQjnKGMDBGwgYKuANK2pAaRryP6CmubWm6qy/YEyCwKi7uSsIh1DDpV3P6box/X7FskU/tvSz1fUX60tV YWNOpuFhxpTlmmUPhtPaKsrL9WX54Z5mGyCqYrtbY7K0RGyhRLdbc1Uj3HQxQkKdO/MxYQ9V3hZy6k7 c5ZfW1V85dbHxoOqwwE5BNdbHUjJk58SNBMsWS8JzL1fX11WejFpG6VTCTRsvlyNs/fCMt2MlpZXorM5vO28/UljueHmlKDlQ4L4v uqy /kpuFDMJffiGbv7ddiBGCXKXgJXTYVIS87IxCYxTKt5qAPNbpyTKx3XR3hqjGX uCNgAATMCtgqIpodu5seE rnJHRxIhctcn8BNOW3MRI7RFUx9W5W0xsdtsX6Ipb5bmb7zI183hVSqcPdZGVekX0untfev5UR9vNBDIXUgnTx8g9YlXOGmZ7kCUv356x2ZLpRuQpbpbMhkIVnd5mv/NK3uLowLWeBMShUei7bmdRhNUVtujbbUhe8FrlQ0Pdp1Ye86f0PZvZeGRpzu0K8c8e695oRiBEd9 3iok2LF0ZtqY2jGGWn7a9K3B893lsmcFwTvyKwdMExI0wKA8IzGK7nF02FUQt3B5nuYs2ylVMYHUw9KIr1d/SEgHnVsjk/AkoDGj8CnIAACICASAQhIJJBIBgRAQDgBCEg4M0SAAAiIRAACEgkkkgEBEBBOAAISzgwRIAACIhGAgEQCiWRAAASEE4CAhDNDBAiAgEgEICCRQCIZEAAB4QQgIOHMEAECICASAQhIJJBIBgRAQDgBCEg4M0SAAAiIRAACEgkkkgEBEBBOAAISzgwRIAACIhGAgEQCiWRAAASEE4CAhDNDBAiAgEgEICCRQCIZEAAB4QQgIOHMEAECICASAQhIJJBIBgRAQDgBCEg4M0SAAAiIRAACEgkkkgEBEBBOAAISzgwRIAACIhGAgEQCiWRAAASEE4CAhDNDBAiAgEgEICCRQCIZEAAB4QQgIOHMEAECICASAQhIJJBIBgRAQDgBCEg4M0SAAAiIRAACEgkkkgEBEBBOAAISzgwRIAACIhGAgEQCiWRAAASEE4CAhDNDBAiAgEgEICCRQCIZEAAB4QQgIOHMEAECICASAQhIJJBIBgRAQDgBCEg4M0SAAAiIRAACEgkkkgEBEBBOAAISzgwRIAACIhGAgEQCiWRAAASEE4CAhDNDBAiAgEgEICCRQCIZEAAB4QQgIOHMEAECICASAQhIJJBIBgRAQDgBCEg4M0SAAAiIRAACEgkkkgEBEBBOAAISzgwRIAACIhGAgEQCiWRAAASEE4CAhDNDBAiAgEgEICCRQCIZEAAB4QQgIOHMEAECICASAQhIJJBIBgRAQDgBCEg4M0SAAAiIRAACEgkkkgEBEBBOAAISzgwRIAACIhGAgEQCiWRAAASEE4CAhDNDBAiAgEgEICCRQCIZEAAB4QQgIOHMEAECICASAQhIJJBIBgRAQDgBCEg4M0SAAAiIRAACEgkkkgEBEBBOAAISzgwRIAACIhGAgEQCiWRAAASEE4CAhDNDBAiAgEgEICCRQCIZEAAB4QQgIOHMEAECICASAQhIJJBIBgRAQDgBCEg4M0SAAAiIRAACEgkkkgEBEBBOAAISzgwRIAACIhGAgEQCiWRAAASEE4CAhDNDBAiAgEgEICCRQCIZEAAB4QQgIOHMEAECICASAQhIJJBIBgRAQDgBCEg4M0SAAAiIRAACEgkkkgEBEBBOAAISzgwRIAACIhGAgEQCiWRAAASEE4CAhDNDBAiAgEgEICCRQCIZEAAB4QQgIOHMEAECICASAQhIJJBIBgRAQDgBCEg4M0SAAAiIRAACEgkkkgEBEBBOAAISzgwRIAACIhGAgEQCiWRAAASEE4CAhDNDBAiAgEgEICCRQCIZEAAB4QQgIOHMEAECICASAQhIJJBIBgRAQDgBCEg4M0SAAAiIRAACEgkkkgEBEBBOAAISzgwRIAACIhGAgEQCiWRAAASEE4CAhDNDBAiAgEgEICCRQCIZEAAB4QQgIOHMEAECICASAQhIJJBIBgRAQDgBCEg4M0SAAAiIRAACEgkkkgEBEBBOAAISzgwRIAACIhGAgEQCiWRAAASEE4CAhDNDBAiAgEgEICCRQCIZEAAB4QQgIOHMEAECICASAQhIJJBIBgRAQDgBCEg4M0SAAAiIRAACEgkkkgEBEBBOAAISzgwRIAACIhEICgr6/67E0IoCQ5MEAAAAAElFTkSuQmCC[/IMG]

---

### Post by powerserg19 on 2021-05-25
I get this now
Could not find platform independent libraries <prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
Python path configuration:
  PYTHONHOME = (not set)
  PYTHONPATH = (not set)
  program name = '/usr/bin/python3.8'
  isolated = 0
  environment = 0
  user site = 1
  import site = 0
  sys._base_executable = '/usr/bin/python3.8'
  sys.base_prefix = '/usr'
  sys.base_exec_prefix = '/usr'
  sys.executable = '/usr/bin/python3.8'
  sys.prefix = '/usr'
  sys.exec_prefix = '/usr'
  sys.path = [
    '/usr/lib/python38.zip',
    '/usr/lib/python3.8',
    '/usr/lib/python3.8/lib-dynload',
  ]

---

