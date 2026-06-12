---
title: "Get segmentation fault when running glxgears on wsl2 and Ubuntu 22.04.3 on Windows 11"
date: 2023-09-03
forum: General Help
---

### Post by quantumkid on 2023-09-03
I have wsl2 and Ubuntu 22.04.3 LTS installed on Windows 11. (See further details of specs below)

Everything seems working fine beside for glxgears which comes up with segmentation fault every time I try to run it. (The glxgears window will appear for a second, then disappear and then I get a segmentation fault in my terminal window). 

[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAQwAAAA CAYAAADeSSWBAAAYDklEQVR4Xu1dC4xVxRmefeHuBmlYoIm0tqkvalFIqqGa2oSkj4iJGltFW6qgTeOLYFrS IhpTGMU00Kj9VHTaEVtSpCWaBM0tkQgJloDiVCitYCNpYXYDUhCsyzsZbf/N d8586ZnXtmzt17l33MJIS99875Z af b/5H3P aZk6deqQiiVyIHIgciCAAy0RMAK4FKtEDkQOaA5EwIgLYUxz4Omnn1YbN25Ur7322pju52Tp3IgAo32RIM7nlRr49WRhVxznaHOgmYBx eWXq3vuuScb0gcffKBuvfXW0R7iuGpvRIDR/bKMtUupE79UqvJq XEDcFrPl2f/rNTg38o/X aJtsuU6viutHdu8tTgO0odf0KpoYPJ5 7X5bs9SvXfWaWK/k35UX58Hbcp1b5QgLJH6h1L k06U34sv10uNFYOH0 ntNUyQx65Qf4/Q6nTpJ3WCxP gU7lrwK8v632h3VazknbQp/R1i SOhjPaT9NxtF///A V7ZIvx qtlWLDp9E39sW5Nsa2KjUyTeTGuSFzXObZ2XmpKju3XffrS6  GI1a9YsXW3nzp3q1Vdfbaimcf7556urrrpK00dbhw8fjoDhmcARAQaEp00EkIu47GKhgNULOKHtQTA7HxRBE8E8KQKmOkUAviLC9u8qQIQABsbb8W2hczih0yqg0SpCNvQfkfmbE HsEm0Lgu0S4oHfCTAIMKEOgALCPii0Ws9OgIxCjnF1CXi0fCahNSj0W VvjEPTFkBCmXJfAl4mQAGYWj8r/ZG AliC6KRAB Ef3GeMS/oGgDMBg3XI 6FDAnRrQ2cirN4tt9yibrrpJrV//37V2dmpBfnMM8/UDy9dulT19vaGESpRC5oMStQwipk2IsAoMR/OqqMFGFqwBCAgRC0z5d nEiHtWCJg97NkFw0BDGhUAJ1 0TqomXAMAAMIjkvLMLULMKJjaSKY3L01QKxLWEQBBTign7k6KYj0fSupmwFUCnwd1wntH0o/fiP/XkrqhNAhyPRdXZ0mghH5Qw2jIq6EE2tGOvPFzz/66KNq/vz56rrrrlMPPvig9mHs2LFDzZw5U73//vtNaTwCRhhbc4ChF3Z3stNhJ8UuiN2zsqm6AF2qKRew2SSEQvs4oLpLMU0AClWtLpIehBgFO/qJx0UYf5DsuvxMYYKgtH/HbSZQGE/uEuHbJmr8T5JxYeHDfKB24wMM0IF5YguM1l5WV00DW8sgvwgotcashVa0DBcvCQ6dYvoN7c1rLwQJjAM8x45vmlV2e ifTQfaF8ZBrUSPNQVZgogJGIOpzNYyQ EbWLFihXrnnXfUAw88ELYSjVqrVq1Sl1xyibr33nvVsmXL6nZ6wpxZuXKlpoXy9ttvq08  UQtWrRILVy4MNevIsB44YUX1IwZMzQtAhZBDX186623tOkU0ha0J7RPUwt9Wr16daY1wUx66qmndN/6 vrUnj17hpliW7aIgEqBprVmzRp1xx13aA2Mn9EfFJh1F1xwQaad8RkAcb1lGGBg0WqVWwQMBTszClRsqMNYWO3fTL6jKm0vci5iqu40AfAZqjt9F3yeqjkHwR0MwGLWwe DfYkaTjPAbitT3Q1/BMAAAtX DaEnPoGBFwVcZJygM/DHxGnrA4yWqcnu7TKf7GdNLWMKtJrUd1E0SdAwXMIOfrd9OR2zjP04TKvU70J6BBs9Tw7/iZ6rAjraXyLzi35qU0tAGcBc UPxRgHfi afZZLQpIDf4a677soNe9b8O9W0LyxSg5U 9b/9W1XvTkFKKfOXH1VH/rFBffT6zYrOSAgMynPPPafWr19feo0DBObMmaPgzPzwww/VWWedpXp6erSwlgEMCDGEGiYSTJbly5era6 9Vm3YsEE9/rjsZFJC2lq8eLEWbgj29u3bVVdXl1qwYIE6dOiQuvHGGzUd068yffp0dfbZZ v AkQZKQIQYCwYGwBHz3t/vx4T gha7CM 7969O Md2n722WdL85IPOAHDFArsWlDdKVhmSxQMGzBgN2MXp3qNZ0iHKi6 CzFJWMfc2c3dmH8Ps MFEGjrQwPQO/BiEQgBEjoDu2Shk64PMOCcNTUSkw uZ7WJIQIFwTNNBNdMZaZEatawDrUXfCb4Dvx OGBw97cdoGXo5Jy58iC0zMqfqs5bOo1PyqYx9JGM69NVLdScU7Z56aWXqr179w7zN8y77WPV0t6tKsd6VXvXLNX38XbVf2i36vnSsgwwQAPPQ7uAUKBgV33iiSeC/RcQspdeekmDhemXwHdlAQPtU9ghoPPmzdM7P8EwtC1oKvDJmDs8wZWair0 SBvjN7U1gAY0FTiCH3nkEf0YQQvAYWtAdSOE9aATMGwAgEC4bNdagEFTwtVJE4zKAEYtx6hLWE26GpjSSIdtUpjj8gGGFhABzhANwwRIXxRBRzvETKL25eIZNIB28VvATDQdtawLQNQRF/hXUk2wDB2aJMd/nvhMzChOET0CXahfA9rF7K tUr3v/kodePM Nfuyh9T0OTdo4BgSjeOfm76njv5rc67rEAJqBdw9QxY/tRRToPAchA4CVUbDYHs0lbBLU1PAb6Ft0ZRw9Z8aBADi uuvVxdeiAlNCrUkE/gIGKbmYdIFwAFwu7u7tdaxb98 9d5779WlqZl0mwYYMF8qfxnOmpPvVndIRh2KoiQ UPEBxtDRJPxIDQOmDIRA xo8GobpHyDw2MJBOjXDmwVOQhMs sVnYJsaNvdcURFTO4GmoceXRlFqCZZNRwPnlkTzYsl8L6nJpmkLL00nrM1DnyCf/rmvq54vfl8d/vuLOWDA9zZQkBbPYcAPASGvtRPbbYcKsdkO/i6KkhBsRgIYDA/b/YVTF3TpL4H/59gx2QGkQJOwNSUfYOA5gM VV16pzjvvvMy0KQO6rvn0mySp572MhqFDeeLsNJ1orsZDHII wPCZJACuzIfx1WQnhnmFcDBCohwXIxm5CEgatswiKQFRElvgXHyDoOFMCEwcaCAuv4SLX9QkaH5lDszU0ZmZj0aUJISOC3QzIKKPJx27y8x0mau1TBIfqHChM3RqA0atHdWmS eh7UcpMkmwk9uaB nSJIGWgDom3dC2CAa1QsMEuSeffDLTBGqZOyGAYfOEgBcKusGAgV0Ktj6KdnqKP4KLFIsSzjGU7PxAemoX3nN4zrNISnqwCWcNdJHzD YuxogCfsLBJdWfVIPjreX05FCX7Ri1D3kFOT1lsVe2JgfEoH6bURIKdHbGAmOHc9c6Y4F EbxqncMwGVwUhjRNCPTLLOSh7qcU8q4NYVacyzCcuXboU7M4PSBG4AuhQ9DNzlik51RAjyYJx 6qY28MRU7P/GjdnyDUcOJBjZ47d64 hwFhhhP0iiuuCCGh69Cmh3AfOHCg0OlJYaKDFA7Hl19 WUdAyjg9i9oynbm7du3SERsUOD/RPoEHfUAoedq0aVpD0PMqvo tW7dqvxBCzqbTE3ReeeWVXMgZgAK61FIwHvheUMrw0Ga2U8NACJAhUQiH6S03PfI2MXM3xfM6KlE1xYadSsTzqAdnJISBBTs6Th1iB7aLy3zxhVUhNDjpCCFCAQiZqjXbyJ12tE5xsk7RSU zr4WAkYZQXSufPGRYU58ElWI7PUNPevrogLbWeCR61SbrKQuDC2iaJz1Rz3calOMZaVgVwoPoAA9rMby4bt06LcChBbvz/fffrwUMBdoBBMgVVrXrQsN55plndGQiNKwa0hZ4g/bZJ/QLjlQeUTfDrugDfDCoy/r4jOftYmte9LewXr08tNsJ8mGETtBYrcdogz5TskWE778iGBIm5eGmsdrv2K9ES2jky2eMHtQyPRrJ89Fsq5H9LqI1KQADDMhpISlHah2SGi3mx3b8HGgkYECLWLt2be7cg78H9dUYzbbq62F9T00awCB7oMrDP2J7/OtjX3xqLHMA6j1PVNKGR5jRdCo2qv j2Vaj lwPnUkHGPUwKT4zPjnASAJ6D38AHJ NfuOVnBnNtk7lbJzSl89O5cBj25EDkQPlORABozzP4hORA5OWAxEwJu3Ux4FHDpTnQASM8jwLfgIx93POOSd7ozH4wSZVRH WLFmSnW9wvU1ab9Mx3V29nBtfzw0DjNFIjXYqWIQFjcMv9om4sn0pQ2fTpk365Z/Q48xl 1KmPo5qP/zww/q0JN9TGOmrzmb7ZdLdleFhmTHGus3nQA4wzNRoeIfePE7arNRozR9i0kI9Z 9dfStDBzkJzj33XJ01qhlp5crwzkxKU a0ZJk2WNeXvaoMD tpPz7TPA7kAMNMjcYFjjh2M1OjNW9oecqNWqSNojNa4zaFGNoOE7U0s/0IGM3k7qmlnQOM0F3Il2bMl66M9i6TkYAFyF6ELEYoZio0X1tYnBCEN954Qz Pv/HyDrI0YSc14 MuVvOIsC81Wigd25ZHm65jyHj7EYlUwCuYCXgZyUzV5htX2WVTJMS saMt1/O1aNb6PpSHZccW648eB3KAYb5NhzfjXPZ SJoxX7oytgPB3rx5s05Gwrf8zCxC9bQFMwq5E/jeP 1l  0 spjZinyp0eqhwzZtwLDHNXv2bO1fMXMe2Dy0xxWyRNhn1EUafRSkhmPh/PrG3ijACOVhyNhinVPDgWFOT19qNF aMbx 60uNZic3wVuEOIEH0MBbe8yS5GsLGgQF6/bbb89e76WmZApqWVPClxotxJHJNl3ZnfC6ttlnexyh4ypaNr4dvdYYXGNvhIbBvpadi1MjGrFVFwdqhlUh1Ndcc43OQ2Bm6fGlGUMjptCzUTM1Wihg NrCq8dmHkN7QZYBjEalRjOZXAswMC5fBqXQcYUu6yKTJGTsETBCOT2x63nPYdhZerDYi9KMXXTRRQ0FDF9Ks1DBYhblWrtqaGo0H53xCBghY3cBBp6D/8VOa dzepbh4cQWv/E3uhxgYKexw38EDAqaL81YSLqyUA3D1xZtazu1mmtnZ5vPP//8sDTrZVKjFdGxp78RJolLS6onl0MtIQ4dO52wjLLUSh1Xa05M3pTh4fgTqYnd4xxgmKnRkJmIjjYzNZovzZi5YGqlKwsFjDJt QSL QnQPzPB6rZt29SRI0f05TFFqdF4/0QRHfhUzNec6fSETwYF/IAZVcbp6RtX6PKsBRghaeEwdvqFzDlF28joDQc5 YPvitLd4XcfD0PHFOuNPgdygBGaGs2XZsyXGi0UMMAOX1uhJglpmUej8R0TovpSo5mCax xNumwP66pNFPeh4RVQzSn0CVTZCaEjN2cU2wgjz32WObjQh9M/hSlu2N/i3gYOqZYb/Q54PVhNKpLEzFdWaN4E lEDowXDowKYEzUdGXjZZJjPyMHGsWBpgDGZElX1qhJiHQiB8YLB5oCGJMlXdl4meTYz8iBRnGgKYDRqM5FOpED9XLg4MGD6owz5MKVWBrKgQgYDWVnJDZWOBABozkzEQGjOXyNVBvEgXrvJYmA0aAJsMiMCDD0dYqflxvEft2czkWqkQMRMMbWGhgRYHTLJce4 9N132nIMAE4uHDZvmA55NmydXCBEW5Mb5Vb21EG5cLn43LH6dDB5LPrBnPej2qOr huVV5YzIurzT7ykmTcfo67TE 7M713Fnenyj2uuIx6QG69Z39YB3fCmvedHv9FUif0blUfHfbRd29qdsG2xXjzcuiyc1JUf6SpIqOG0cjZqNIaEWBAeNpEALmIy3aRAlYv4IS2p 9WlQuZh0QwcTM8bpHHrfSD/5YLmkVwQwEju FdLqgGHfuGd95GPygXGePWcxYKGy65rrwuGAuNTIACoIXb2XlDPe595e32XQIe rZ2oTUod8K2yt8Yh6a9MqHM29tNgNKXZX9WMEjmBsASROfHycXXvJk9G5f0DQCHwjFkt7engxs6JEC3NnQmwuqZqSJxazlub fFzKGpIiNghPG6bK0RAUbZxuz6owUYvMEcQtQyU/59KhHSjiUCdnJTPG5yD9EwoFEBdHALPDUBjgFgAMFxaRmmdgEedCwV4dyXv0G a13CHQoowAH9NG Zp/DzTtgMoFLgw/2xHT UfvymetF0CB2CTN/V1RkiGJE/RbfRj3Qd2M bqSKRDxWXMe/YsaNUqsgIGI2elYTesKsSW7qTG847vp3sgvrG803VBehSTV2XGkMotI jJ2nINAEoVLWGRHoQYpQh2elOPC7C INk1 VnClPuomURaOzCprkBYTy5S/5tE1PgJ8m4Kq8luyq1Gx9goB9TBCjw3Ik11Z7zZniMD1qFrWWY2kXRTqyFVrS1WhdEg27nL2Xse/PaC0EC4wDPseNTa3Lx10UH2hfGQa1Ej/W RAsjiJiAMfh QrmSvFM3rOA9kRUrVuiX/PB UtlipopctmxZXbe3R8Aoy/Ww s67VSGQEDAULBoUCAMEEQur/ZvJd1Sl7UXORazpGCYAPh 7OQES C74PFVzdpkCCWAx6 D3wT55fmECZKBlt5Wp7nvy5gYEqv0bQk98AgMvimCLcILOwB8Tp60PMFqmJru3y3yynzW1jCnQamZUNYda0wJQcwk7 N325XTMMvbjMK1SvwtpEWz0PIm5gnmySxEd7ecA2Ek/takloAxgrvyheKOA70XzzzJJaFK47j2ZNf9ONe0Li9RgpU/9b/9W1btTkFLK/OVH1ZF/bFAfvX6zfuEQSZjwkhsK8rOuX78 bEWntSJglGJXcGUnYOScfLJrQXWnYJmUKRg2YEB1xi5O9RrPYPczTQB8F2KSsI65s5u7Mf8eZscLINDW71ydCHrHYhEIARL4CbQmIAuddH2AAYAzNRKTD65ntYkhAgXBM00E18xkpkRq1rAOtRd8JvgO/H44YGT hVTLcYEFeFBEJ fMlYrQMit/qoIPncYnBYyGPpJxfbqqhdJsMdtFqkeka7Tzq8y77WPV0t6tKsd6VXuXJED eLvqP7Rb9XxpWQYYoONLFelb4REwfByq7/eg29shELYqbgq8DRg0JVxdMsGoDGDUcoy6hNWkq/sppgSet00Kc1w wNACIsAZomGYAOmLIuhoh5hJ1L5cPAO4tX8rEVDTUcu6AAOACwCKmmAZOjRJjv888ZmYUZwiegQ619pwtQ/tYvbXVqned3 lDrx5n5p92UNq pwbNHAMicbxz03fU0f/tTn3KMKqyLmBFxjNVJG 5R4Bw8eh n5vGmBALa78ZXinTr5b3SEZdSiKkvhAxQcYQ0dFIH9a1TBgymS Bo GYfoHCDy2cFBToQ DIw5xEppg0S8 A9vUsLnnioqY2gna1ONLoyi1loRNRwOnaBSM0OC5zPeSmmyatvDSdMLaWppvCZ7 ua rni9 Xx3  4s5YMD3NlCQFs9hIBM8cm4wf4mvrQgYPg7V97vfJEk972U0DO3NF2en6URzdS/EIegDDJ9JAuCCQGgfxleTnRjmFcLBrQuqmhMjGbkICBx/C41ISkCUJAQwIGg4E8JQpssv4eIXNQmaX5kDM3V00uzzmUA2HRfoZkBEH086dpeZ6TJXa5kkIcvUTBVpA0ZItna0EQEjhNPl67idnrJLwdbXOw2cnuKP4CLFooRzDCU7PyCRAxR4z E5zyIpacQCZw10kfMP5i7GiAJ wsEl1Z9Ug Ot5XS3Y9Q 5BXk9JTFXtmaHBCD m1GSQiE2RkLjB3OXQE8AAqdq gXwYv BFcdTkGRhmGaEOiXWchD3U/wNOVdG8KsOJdhOHPt0KdmsfgQMT8EvhA6BN3sjEV6TgX0aJJw7K469sZQ5PTMj9b9yUwVOXfuXH0OA9nHzFSRPjoRMHwcqu93J2DgTAFDohAO01tueuTtJk0tBM/rqARs67TYaju Rj04IyEMLHCitYmwYge2i8t88YVVITQ4MQkhQgHQmao128iddnSEZ1Gv6KSn2ddCwEhDqK4pIw8Z1gS4odhOz9CTnj46oK01Hok4tc3Lnyod2Jjnk 80KMcz0rBqaKrIoiUfAaM QPA9FeTD8BEZ678z2qDPlGwR4fsvDqBUQ4Zjvf TuX/xXZKxNfuTAjC0ZiC mPbvVHdQfFfrkNTYmqLJ3ZsIGGNr/icNYJDtUOXhH7E9/mNrWmJvRsqBaJKMlIPu5ycdYDSHjZHqWONABIzmzMgpffmsOUOKVCMHIgeaxYEIGM3ibKQbOTABORABYwJOahxS5ECzOBABo1mcjXQjByYgByJgTMBJjUOKHGgWB/4PscrLuLvDsIgAAAAASUVORK5CYII=[/IMG]

When enter $ glxinfo I get the following [information]("https://www.dropbox.com/scl/fi/wtafxa4rek65gncrrmgo2/glxinfo.docx?rlkey=pj4n3is8o8pog556d316mu8g5&dl=0").

I'm stuck on finding a fix. I appreciate help of what else I can try, if  needed I can send more information. 

Device name:   HP EliteBook 840 GB Notebook PC
Processor:       11th Gen Intel(R) Core(TM) i5-1135G7 @ 2.40GHz   2.42 GHz
Installed RAM:  16.0 GB (15.7 GB usable)
System type:   64-bit operating system, x64-based processor
Pen and touch: No pen or touch input is available for this display

Edition:    Windows 11 Enterprise
Version    22H2
Installed on    &#8206;01/&#8206;08/&#8206;2023
OS build    22621.2134
Experience    Windows Feature Experience Pack 1000.22659.1000.0

---

### Post by TheFu on 2023-09-05
I'll reply since nobody else has.  Usually, just after I show my vast ignorance, someone smarter will show up. ;)  Let's hope that works.

Use a real hypervisor to support better GPU.  

My understanding, since I've never seen Win10/11 in my life, is that WSL is a minimal Linux meant to support Linux containers, not a full graphical OS.  

Plus, there are many levels of what a "graphical" OS can accomplish.  Typically, a VM isn't meant to run gaming graphics, but is sufficient for Solitaire or using office-productivity programs.  

If you want gaming performance, you'll need 2 GPUs and a hypvisor + motherboard that support IOMMU to pass one of those GPUs through to the guest virtual machine for EXCLUSIVE access. That means it cannot be used by the VM hostOS at all, hence why 2 GPUs are needed.  The GPU usually needs to be $250+ alone, so at least an nVidia 1060 or higher GPU is needed for passthru.  I don't know AMD GPUs to recommend one.

Laptops need not apply for these uses, unless they have high-end 2nd GPU. This is typically found only in $1500 "Gaming" laptops.

---

### Post by quantumkid on 2023-09-05
Thank you so much for the reply. 

I want to install a simulation called GEANT4 on linux. I was under the impression that I needed to check that glxgears was working or else the installation of GEANT4 would not work properly. I suppose I'll go ahead and try installing it any way and see if it works.

---

### Post by TheFu on 2023-09-05
[https://geant4-userdoc.web.cern.ch/UsersGuides/InstallationGuide/html/gettingstarted.html#softwarerequirements](https://geant4-userdoc.web.cern.ch/UsersGuides/InstallationGuide/html/gettingstarted.html#softwarerequirements) has the system requirements. The base system just needs a C++ compiler and CMake.  That's a pretty low bar.

For visualization they specifically refer to an nVidia GPU.  That's very different from what an Intel iGPU provides. They aren't even in the same class.  The visualization part of the software uses Qt5, which means you really want to run Kubuntu, not WSL.  For higher levels of GPU, they mention using OpenGL which is where glxgears comes in.  Meh.  Also, be certain to use X11 for the display server to will avoid some issues.

There are about 10-15 other graphics libraries that are listed ... not as dependencies, but it is unclear why.  "Nice to have"?   IDK.  When it comes to that level of GPU and graphics, you don't want to bother with virtualization at all, especially if you are this new to Linux.  Try a dual-boot setup and hope for the best.  If it were me, I wouldn't bother trying on a laptop without a dedicated AMD/nvidia GPU.  The chances for acceptable results are slim with any iGPU.  

Getting all these separate dependencies installed and maintained will be hard enough.  Also, the Linux instructions aren't for Ubuntu - they did it with CentOS (which doesn't exist anymore).

Is there a reason you don't just try to get all this working on MS-Windows, where perhaps you have more skill?

If I were going through the effort to get all this working on a Linux system, I'd use dedicated hardware and use it only for this single purpose. The typical desktop/laptop Linux setup with the necessary security patching every week will probably break this delicate setup of dependencies from time to time.  It is too bad the project team doesn't make a .deb meta-package that would handle all the required dependencies automatically.  There are lots of very complex software with 50+ dependencies that do these things to make installation basically 1 click and perhaps 3 minutes of time.  Learning the packaging takes time, but use of software at any scale requires it.

---

### Post by MAFoElffen on 2023-09-06
You have Windows Enterprise, and two GPU's... Will get into that later --> You have options, but not through WSL...

Do not do it with WSL2. WSL2's kernel is an extension of the Windows kernel which simulates the Linux environment, but is not a true Linux kernel, so you are not going to get there from here with that. I could get into more detail, but WSL is a terminal emulation, not graphical. glxgears tests the framerates of OpenGL (3D Accelration). Sideoe, there is a Windows version of glxgears.)

Like I mentioned, you have Windows Enterprise, and two GPU's. As I remember, 11th Gen Core i5 is a 80 EU Iris Xe Graphics G7 iGPU, which is rated for light gaming. Install the Windows version of the Intel XE Client (not datacenter) graphics drivers on your host, in Windows. That graphics driver has hooks that virtualize the Intel GPU to be used as a virt GPU passthrough for Windows and Linux VM Guests, without the indepth vfio-pci drivers, and the Powershell scripting that usually involves. Most everything is taken care of in their graphics driver. 

Then add Hyper-V as Windows feature. Install an Ubuntu VM as a Gen2 Hyper-V guest, after you install the Ubuntu Guest, install the Intel Linux XE client graphics drivers to it. That will passthrough your iGPU. That is the easiest way, and get you where you can do 3D acceleration very well with that iGPU. Like I said, light gaming. There is some lag, and I'm still playing with the config's... I would hate to say this, because Lunar is an interim (rolling, not LTS) version, but it seems to work better with 23.04. Intel is still working out the rattles in the Xe Driver, So I hope by the release of 24.04, that it will come together more seamless.

Note that passing through a GPU in Windows (and Linux) usually means that it is not available in the host. So it depends where you want to use your NVidia card the most, if you decide to try to paa it through. How that was done in the past was something called RemoteFX. That worked, but not well, so they abandoned it altogether. What they replaced it with they now call DDA or Discrete Device Assignment:
[https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/plan/plan-for-deploying-devices-using-discrete-device-assignment](https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/plan/plan-for-deploying-devices-using-discrete-device-assignment)
[https://learn.microsoft.com/en-us/answers/questions/303104/enabling-discrete-device-assignment-on-windows-10](https://learn.microsoft.com/en-us/answers/questions/303104/enabling-discrete-device-assignment-on-windows-10)
[https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/deploy/deploying-graphics-devices-using-dda](https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/deploy/deploying-graphics-devices-using-dda)

I followed this guide:
[https://www.techtarget.com/searchitoperations/tip/How-to-deploy-graphics-devices-using-Hyper-V-DDA](https://www.techtarget.com/searchitoperations/tip/How-to-deploy-graphics-devices-using-Hyper-V-DDA).

One note for passthroughs, do not let the host nor VM Guest go to sleep. Strange things seem to happen, like it losses some of the connections between.

If all your need is OpenGL, then if you create a Hyper-V Ubuntu 22.04 Gen 2 Guess and turn on 3D graphics acceleration... I use KVM with VM Guests using the VirGL driver for games that just need OpenGL. If in Hyper-V, a Gen2 guest, ad turn on 3D Graphics Acceleration, that works also.

What do I do most? I game to relax and unwind. I dual-boot Windows and Ubuntu, so that I can run on native hardware.

I am investigating this: [https://github.com/jamesstringerparsec/Easy-GPU-PV](https://github.com/jamesstringerparsec/Easy-GPU-PV) <-- Jury is still out at the moment on that.

---

### Post by quantumkid on 2023-09-10
Thank you so much for all your advice. I will study them carefully.

Best
Peter

---

