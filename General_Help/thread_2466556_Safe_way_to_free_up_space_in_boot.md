---
title: "Safe way to free up space in /boot?"
date: 2021-08-30
forum: General Help
---

### Post by lainsquid on 2021-08-30
I'm having trouble free up space in my /boot location. I've tried using the autoremove command but unfortunately  that was unsuccessful. Would it cause issues if I rm initrd.img-4.15.0-155-generic in /boot? I'm currently on 4.15.0-148-generic according to uname -r. Any help would be greatly appreciated! 

currently in /boot:
initrd.img-4.15.0-155-generic
vmlinuz-4.15.0-155-generic
System.map-4.15.0-155-generic
config-4.15.0-155-generic
System.map-4.15.0-154-generic
config-4.15.0-154-generic
vmlinuz-4.15.0-154-generic
initrd.img-4.15.0-148-generic
vmlinuz-4.15.0-148-generic
System.map-4.15.0-148-generic
config-4.15.0-148-generic
[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAARYAAADSCAYAAACPQ 9ZAAAgAElEQVR4Ae1d25HrOg6ceJyKI3EU 6XaOBSHP24I 7lhbAjaAkiQ4AMkJcsaadSn6pQ8lkiCQKP5MAH9LPgHDfyyBv7zn18WAM3vroGf3WtEhdDACg3888 y/Pwsy7//vaIQHj29BkAspzfR3xbwf/9bln/9a1n9 /3c 79Q7EcjeLo7/QwAEaALEcoGQ0AQ3cTQMglrtZHP2FBg7QAIjlACWjCWjgbhoAsdzN4ugvNHCABkAsBygZTUADd9MAiOVuFkd/oYEDNABiOUDJaAIauJsGQCx3szj6Cw0coAEQywFKRhPQwN00AGK5m8XRX2jgAA2AWA5QMpqABu6mARDL3SyO/kIDB2gAxHKAktEENHA3DYBY7mZx9BcaOEADIJYDlIwmoIG7aQDEcjeLo7/QwAEaALEcoGQ0AQ3cTQMglrtZHP2FBg7QAIjlACWjCWjgbhoAsdzN4ugvNHCABkAsBygZTUADd9MAiOVuFkd/oYEDNABiOUDJaAIauJsGQCx3szj6Cw0coAEQywFKRhPQwN00AGK5m8XRX2jgAA2AWA5QMpqABu6mARDL3SyO/kIDB2gAxHKAktEENHA3DYBY7mZx9BcaOEADIJYDlIwmoIG7aQDEcjeLo7/QwAEaALEcoGQ0AQ3cTQM/Pz8/i/x/Tu9lfj3C3/L96PXT8mPtPJfp/V7e82u1nMfIF/VZ9sfLPj1Xyf54PJfna1rm2bDP47XMpJPwf1qeyq6lHKWMD1// z2vxsB 8m3Tz0j/zvDM7 OvtPsX9XJMY695PdjtTj XaQOx2PUdoYPH8prn5fV8LfNKYglyP6e60xOxbK2TCCiv9zkt03ODTvJ6hNyG5NtBP9IerqsGroCvffXmgCWjXT5jebxmHgnnaYqjYk4SzymMlnn5n2I0dSOrBi4xObVPZXlk5hmJIqIHEYmMyPMyPVcSiymfzH4mX/ 0PMk58vZ/VPvU95frb9HXhmGeE8n9s7A tpLAR45rEwXJ9nqo 0NEoJ6Xfn8g32f66dgnwc97mafX8vAyD G7UZ6csotfE3 iw8dC/RcfpNn4RIOQtono DpX6dzPQkquOQsrnxzKd5SUYD1X 56U352xsPJnHnkf1M7jufCVnTq2/fPjjbBhxlLtHxOfMyItB95v11YAOstOMw2/RHzQyGosSQyjc7tCJludlupuOW5YBtEyUesr2tcamaivCYhJxg363Srfp/pxM0HbPq9pCkTCOiCimOJSuofvXnmu08Rv1H8Vf0xMNOioLQiS753ZxMCWZdMTfN/vOClEzzAsAFmKo06OEEuVlGrOtBH4Vfl0XQQOTwChz/q GDeRyc96tGPz5zjjkhEtjEh drba Em70W5FPSSzEJnI3Li2iaXfv9D Rvna um037MP3S9sQ7PfaJ9ga9GR7sdAee6/LiP1ZNcq/njgjCQXdJmVveD3EaD1jruZDIgl6ski1iHjr3T6pM4B8Lrn1y0VybET 26VcQ/51rZNz ezq0SOvi6axDLq EmbCiuKIOr 5eSTpVlib1X2gt9HJdQ7vhexxKkd/wLxzqanpmFI8Xpqby2FHu7XIjUS5cao9k8DszZjkaWQrHc3LIUSOUzH6ctvERotBeZX/KXpSftixYylUf/jtUzq10C9DExk7wHdsOGYfB6Hpn4iTnOZeCnUsA/1R snL98mFtpDaZfn oy 67aq PN7NHq2Tr y0Z5iQvY93Z/vfnuqScqQKTx3lNeScbP1hxi9M9Uk5T5I8fJcQhT18olSk80zv3lLdSUjldQTp7jOqPK9bP7KlZ5T98gRfd/IyNJvJ4czNOuBZKefZpUjavC0Puspf1leZMnlj5uDYgcnh54 P5aX2vzTm5NRHrt esbtL2m72o4c63TP6H4FGRPbjMiX9rPUT0uenn3yzVG/l8f97uGb2rXLW/iP BW9C 7kqu2c6ufNvx6qPZfzkcbIr04tg Fe7kT0N80I1gEfeqzp8VvfwT6nwNsphBhhwF99hn4JktG4PiOAHr9FFCP1wj6nw9/pBPpVAhkBMZ4BZoCBLga6D8DRr7nGhd1gt9/EAIgFow8wAAzsjoHdK/xNlkTbGKWBgXNgAMSC0QoYAAZ2x8DuFWLEOMeIATvADr JgR2IpTg0V6 TDlKd /yHP8xUnFqt90dGuf3ykdjtIF KrRuxw6fX8 Pz zr4VIeq/H7CWkeWVWO/yaCdtnfIB2Id695wTD3RWV4v8qV0bLkfphM7YAY0rnd9HJtnE2r2QUeLXba2Xr4SZ0iTWFSd YxFjs5b V7kvhyRFnl1PfKMHGArj7z3gRbiYz4hgZwABIif1OnD6ou0BitnVewgH8j3mX7KI/dko2DDJGQD VL CJlV8rAQAAW45BQ N4SVr0QUYRKLdzDrPhODih9yQV8xVoLuC7HUHCS5/3gu88okOSyX7q98FmIYvbYcV KkOMZJB1WOkV5BLEksTr Omt7EbkUyLmULeuZT/SBfyqB9RnF2jeeo0w OIJbQ7TRaVIWl08zDO13izL6jDMBGcJ51v6grc9De/dRBYhS1 74fBCazID3jCaPpGiNmcge58jpWzmCIaG1i6fcvyLFRvrZ Ou1TX3MS1HLwwBXDJaINYpBe0/4D5bn/us3cHk380mxLB3zekiTGl0BRt05RwXhkAD1ia2CcmVgYYJkDxk6OK4bq0f1fU8cAeAPZrQArOXYyY9sq4x7yrW2bns/7msjRd9yATbHFyvJ7EIsMuoGkRRZcLd8SBnYGTmYrpDQNjF8kFplBPCgZtV6fi4xJKr8 WE2AmI7TyGci4EoAL3ql7HlpPg/kS1H7K34PCflSIl5MbArOrnGNHaKRQZY6rnNqmkujuN EJSfnZ980kqpn9D5CSLjUvi/10BSYR2Xfhrm55/Oh6Pu1qXqaqyX2sWU0XY8QWXxe hGn6HJPlwtT WSUTvNt1KOj7fqpHeRLaeAD VKsWcNvfj/mdOJEuEJfn2IA VJugaFbdPI3mRttc3rPuEFbn7EBh58S9snKw6AnMwiI6Bp7CLBT204gFhALMAAM7I6B3SsEk7eZHPqBfu6AARALRitgABjYHQO7V3gHNkYfMesABtoYALFgtAIGgIHdMUAV5ge4pvIYdpudwN5D vGH4FaGDCDfy 6g/xW80kHK8uDl3 hbhZhd9Kp xSYfm09Ojn7e e5L4Ycc83M5Kgo4CGTI99LW/Q76 fMYuhT JW3Cc6kGWlHsDB/VjwF 4Rh IJ98xjPHGU8oHw9IheP7AgQzH4cf4eexfDAlcAfLP1/8rlx3HH9eJvUeZPcirHl50WtVJWRhntJoY lH4/pZPhMPKCMWieO5Vs6CtK6q0dNb6vtAvs/0Q7FhHl VkI8fE18O xweMqX2fWpbNsqTHiWkg2Yj/PpdSY0hddTCVOQeX/NXuBIeo79pW13oM4HWdUwch09Gyku2qeMFYGh0iTEzRDQURCbERO9pzmN19PO5cl5T9oJ4MuTkQ9WZmJySe/lg8nr576Hyj Wh ktA0dHERC6pTtL V9tVwGH9iKOSPPJZPdOrg 8XdvCEk5N3lk lV3eVWMKgsWKU3Cjfp/pBvpcVNlqLue3Pl0KVxJA5UgEgNWJQ5HEF2Cax5E4hswIJYqT7AnIiLO UBEbt/KbzjJR/6BkLyZ8TSzl6xPYleDCdkb1FfjWihQDFPDp71HiF3kvbsR6ozyvIq00s/f4F3W UT0b8un467Wv7ih61HHQ/YErbKB0YEyytLM/912VEjuzKBFrkK/ogEj rP9jhHN/XwEnGjIpPFZeRTN6JB0U r5mxdBSrgfMVYqG zsvraWesK1JJ KxqCRhzPVh/r3T6BCwD4HXPd3SayZbP0DYvrfaQb61 ND6kX4kcfV3EQcL7wsryqX/U/Ml91yIWme0n9pb XPNaOlYdWI5QeK8hY11yvEk7JhkmGzG1cxLxzO 4/KER08zHoYHTJBYjX0qvPN fwlKINq5pva5J49OlUAIWai/TjbtvyK9BlQA Aph0q/WHfC/pry9NfNUGiUzPvfKfEYvbo9G/FtGvgDkGEwxpTJz3syOWaZqXMBVV ydJh8ix85kMR65OS1Fe7VlQHbS8ClPSYqmUb17N7HyPH5LNT1/JGbl9Bxpif5I3EoA8q2da8t3bLaGM8lIX1Ud7KeyYKnEUkyLlndEbhFn/Ej0ZxtZTfg0kV1Zk1fI78tDloo10usR88/wV9ruiXHb9bB aZXpdl7JFEov1xe/2kS9ugrIdssGr1m78LrMNDVxJeQtfcfOW2mQseYykMtjlfzRGBatSF NA9K6XYfRZ2zm1HyWx1zPo2M o8wt8t0LYjMkv0LldfkrWs6279PnK/US lxU bQyCO9i/L0Q6IpUbmTsIsQsBfEMO93OzH21kE/l7xjitHr6h2z3r1HZCvpe Tpe6OuUwgBhwJZAQN/CwMgFoNxAfS/BXTY81h7glhALMAAMLA7BnavECPDsSMD9A19nxEDIBaMVsAAMLA7Bnav8IzsCZkwqgMDx2LgOGKhE4xyCOv9LmN96Gft9GDT3rL5w0rVk692W8iHYuvmSiP99/H1N/S0k00PUoYcnT WNdUoRSEJdKLROlI/oAfrgKB5TH gTtJHXu9zUieKB uo1SO6HpJvB/1Ie7gq3K2w39/SG3U8P7Kc54NIjxxTtLHkq5Dj8HMjn0V6wK5y2Kx6jFobpDyynR651s/WP9NsiY9sDzlZvY6CAAQIn9Tp31380iECW vLCWqFfJ/pp2OfRj6TEfy08qnQ6Cr4otku8qEY2BUsHHclw6RBhGzIPFYmAT4BKcajMDhU/A/VVyxpyFk6J1epnqIcxyKp2IkHjazrlkxcryx/tjotGaTluCpO5K10MTKtJH0VxNLRVbXejfJ9qh83E/TR4RX7NPPt CBArbMcP73yrAsenHyMGWH18QyBpaIrC189/Et5XFeRliMJU2mGI2pnIIPFYEDDAbcSS61c4kD9IC8Z0eL zjpiCrpJ2m0o2dBZqCcbNbQu Zmkz/3 hXo3ytfWT6f9RFavEy0H3dekGz7HILwmfgbKc/91m5l RT91Yung36hL6sTV9IN09lEoigwro71SsnaGJjCkTA2Acs9fq4avlRsAUdEPacvoj/m8lKPrcLvrwEqOnRDzVhn3kG9t21379HXRxk /PNtuoO9VfFF0spp9D FAYwKfrf2kfj6IIrqX18zpUihxjJqRawDMjFI3/I/bdJWlWGWqvQoMpuMgHwrr0dSPOTJ17UODkM4Xk9urTSxuqd4qz/XVMDeILyJ2vQT/I/lQLIc/6nsCTLo5W aDSO/XNm9pmcHkUtmI1ZGnYTkSZkGdqTaDg0YV2fSd3AZdkm/DBr0GsZ7yayC5Z0SOOEWXsrpckD/ZA8n0M0XSlTpi3o6yfnrG5fN1fSxla/dvH/niJij1cZ0MPfvkPw5Ivh3kQ4n4aNv4gs9dr0PIt3Fum8E 57bPQSR1DSXoWQ/ybZzPZrDP WxyEIFYSyso5JcNYBkG32d7JLDTpXz1UsLC2eBswMA1MABiwUgIDAADu2Ng9woxolxjRIGdYKdvYgDEgtEKGAAGdsfA7hV kwVRN0ZZYOAaGCBiyQ94Td2AQTD8FkL2h/DC4cCxOv5 PhgVlexfGvcHXznKUdjrDh6O4eOkvuhOP07qJCu9ZrQXiby2M ZL4a/BvjuMkjvkO7GOrW84hp/YL6/34HwwLpTjGXSMA3aXJhSxoyMWisWojhIEWo5IjaH9BAQ 2h6OtecznjkSUyjvj T76NYktsjM1 FH HnyR/qn5UlOQHVYr4FNiGqwvH9fszuuPy/TK4LcHfyaF35ntUTmzlOa5iBpsw4KipfhPn9CAjkBSLuf1HmSfDCa6NYTSxlSkIQlmPiKIQWtfELIB1PHtLZZ5TMVcrEcEt7OJ1sl6I/AWwCaRt8Y8yIjjhATvaf5HUjHCaWfz4Vo5ttgYnKk5uJppuX5kBwyAx0eKv9IcndQ7I0mPiKXVCdp//P 5H zfmT58wkJFHbw/ec KuK WD4Ypy XZ4cJQXQlxNm5Ih/MgB90dJhjdoe/S6FKYsgcqQC4GjFojVwBtkksuVPIrEBemk33haSIsDzoyFm185uKGCn/oIx50THnOSeWOFuTdmL7ErwYy7uZTyTeWpDgprV2offSdiwf9XmFc oUGKG86Nx46Xn6UnMvxx7yUfR6kiiso19tX3EeLQfdD5jSNor2ibas9GOgPOtMtylyZFceYNSWg8MS c5Llg9/6VoDJxkzKj5VXEYymfJ Hg8XqZspyyQWnw/DKbkiiwbOV4iF qoy1PmMZpq0irQRlWdM Qv9rHP6pN4B8Lrn14E1n6H9kM5XEFOQcS/5tM1z/eV/155N5OjrokksPXyKPEmbFRx7zJQDipNPZvtBl1Lvda lY9WB5QiF9xoy1iXHm54 NSEpkJScAVM7Jy1p5vcU9nSa To0cJrEYuRT6ZXn 1NYCtHGNc1eUmL5bCmUgIXay3Tj7hvya2AZ4CXd6nwltEchM7vYdqN mrEpm4b9IN32yOeN8qX4oWX5uyJ/3VmpfxpbNLDx0jXrj9ZP1Imrs00syAeT62vwb0csk341h9o/SSohx85nMmzYaSnK6z0aIRuZkhZLJStfB8nmp6/kjNy yxVCYKAlRyQAeVbPtOQ7D1SjvNTl1vevhR0zz/n7pJHFy1LIb4Ne608viaojF/dVy /q1eXcMos2r/X0Od88v1g GL/8kb4R8a4bwTPb0MCliEX2EKV yjckbWjbM5Y8RhgLoQ4Ln2QfhTHBahWXehlGn7WdU/uV ZDG8KWxdoLPK4Q2RqQTdOKra9NkRBwZufHMV 3Rw9v6X5VW ABsO2rbvlLTEbPcyOwZ sr33c/NMlPRs4S 3q7c76vJru2EfD2nwOYphBhlQTyHERMYuAYGQCxXG50hLzB7AQzASBcwEkbpa4zSsFO0E4gFxAIMAAO7Y2D3CsHakbWhC jirhgAsWC0AgaAgd0xsHuFJkPTic5wSOldxvrQz9rpwaa9ZfOHmaonX 22kA/F1s2VHPL7 PobetrJpgcpQ47O/9rUmI56U0yQdaR QA/WAUHzmP5AnaSPvF7kQzEHp51Aj/q/74cE/vzIMsXL6INw6ZHj2itWW/ks0gN2lcNm1WPU2inLI9vpkWv9bP1ziH/5hARyAhDjfFIn8qHwLLaFH RDqWP65CQruU1iECEbMo V0bE/lZfCc Il/4wLKlT1kQPyjKV9cpXiNmpLITfT8PVVgsx6CuZ6ZfnzCQm0iEXFiWhd9GSj 6SvV6JflSpCyGvk pF8LniPCVt0NdKmBAFKEGrFPs18Oz7qV ssx0 vPOuYBycfA0S6fDxDYKnYwMKXG3QUXgnfCv9SHtdVBOfCtk2lGY6onYEMFoMBK1P7T4ilRkiJA9WDwHSQV23GVCMwUwfiYEm7DSUbOrPq17rkZ5I 9/sX6t1DPh8QGPXTaT R1etEy0H3NemGzzEIr4mfgfLcf92m2Cu71omlg/ sjqBrfN9bTjrFmtGkZNjKCKadoQkMMUANgHLPX6uGr5UbAJEJAKM/5vNaxuF214GViC8h5q0y7iVfTedaD/pz7dlEjr4u2vjpl9 DWEz8677ic49M9H2aiqe/xtCvIDonSRHdW1kKJY6RAMuPYjUAZoaqEotMtWWpUJlqD5GCtGU6bSNfiZSt9cvLp/N9IB9KiicahLR cnu1iQX5UHJ9XeRvcvx0c7bMB5Her23e0trcymehI0/Dz81hFtSZarNTO6LjspQLpci30ViWCCnwXkbMiRGn lJW5IhTdDFgbSmFfCiiN7r27JP/OIB8KIKtP3zVALnGZ TbOLedYJ9z2 cgMruGEvSsB/k2zmcz2Od8NjmIQPS iv4MhfyyAbQx8FktXWGXS/vmpYWHI8IRgYFzYgDEgpERGAAGdsfA7hViBDnnCAK7wC5HYgDEgtEKGAAGdsfA7hUeyYpoC6MwMHBODOxALN3oZNdGfsL3fKOEPyQXDu N6Qb5Wsb0dD57p3KfH5 pvCfX537CWkfyT64AP IhX4tlJ2fXZ5gZ4ADcfj5j6fzy3 vj6nzMXc0 6Gg/v J0nvzrRaflSfEyFKFaeQ2rSSyqzvwoPZVxofq 3qxuuS xSCKvrkeeCeECXEc7RUNuOIpn4TbMWKIBMBmxRPV3YQ/U56e4OuCT5d4q407yrSeW8sg/21xeYepj08RgCk2Bb5WsbxkmP7l/7 Wch42lE5o5ksBwjEPjcFvcyd0xE8JIdL2tminmztZ91n8Kj3IbugtZgfg 4LsbCSMgdJ7j ey5wkqUplrCmZ5dL9lc Z/LWyyXeZXOEe6zDGKencI GZRltVYkne3dzvI7fzkXzI1xJshXwtYfYadFLil0D5WKZ5Ci/iTqKZySkExDTz8E6XOLOvlB1URqGyoZLAVLlh4qAyTQfJkiYZL 1GvpYGGbVmRMjXMuJUeEYYJxAFOa0esa9CLDwryEml4TwV4mNdtJzKKiPfW4Qn98OVlgbjSzVa/iXEu1XGveTTmAh9MnRdezaRo6 LgE1pa2V5tmtSpi5rfWB08iFfS11nwh VqxRwCkxmK2RIDYxfnLHIUu1BybDfab4PljFJJdgHa0URbpQxnRb5WpzOKAXCO8xcTT0KCQzk03FL37g5nNfZJhbka8n1dZK/hVjcXossdZxwkqPEA8lvwpKTk7Fps216qmdC2kHaT5C8Ju37Uo ryy1zwiaeLKv05p7Px0LPCNnIhq6U4 uKGYEYQtcjdcs9zjnC/ZN Rb3pckGGpP0sn830CsvOkfrpGbe/5fZpStmiLLGN3H8vnlj/SNZrTrRnAier/HVM2ng3wtNbtd/LsIwIt3BOtaNUs4sy3X/6oEjJ7ZnoZsMJqhGBDVjkSFfC2387PbdRiEsSNhgJThPwYGoBhDMSAgEBAwsB0DIBYQCzAADOyOgd0rBMtvZ3noDrr7KxgAsWC0AgaAgd0xsHuFf4Vx0Q/MHoCB7RiIxEIHqdYevtJM/2l5XZf92R 4Sw6gxT7Y5co3Prae/c49L7sOmRgw3OXzvYQ 1vuvf4oOh/DkcGQoO2bj79htn7aP8Y99ZN1Bj8cI8qqkWdgu/AdH9n8NqDfO98I6t/ufY6Mes3MMTrdjEvJlujOO0XsHlCP3zXwYjXwrLo5HpQzwx/51UJ0cOafZEr8 lfOpqKPz kj/m1IorCQWUz6Z/fTyzZRH0mlkXTO7o3gY7rMZizQATCuQ7pM6 dWzWfDm1vos Xwbo/3PiSYDbGV50rFPgp/3gnwvA1j7fACOjVgjBZNLI1 KGN4qT/e7YGHn9 /0pRfAP57Lg18ET6CZlqe8FP7Hx5VsWApV5SMn6uSb4cDMp88Ps Gl9NyuLH 2Oi0Z2nJc7oMi70Rf0b5ip/z67Xwvq/q/QT89 7ymmBKE 05EM8XocpJP58hxQZExH1CvPNdp4jfqv4q/QLqxPcL lATVxjpy25347yi01XH6Xs8wLIBb5anzI8RSnQHUnInAtyexSF0EjjzfTK2tRCY/60kCMMnJ44xLZmSyf7B2thPAk7Qb7Rbuyyiz0jnbxNLvX2jfkG9N/wus9fLp9OxD9wvbpPYp2tT9GCjP/ddlxA7Zte4fK2ffWZ1B9 f7PgK03nEX9QxiiXqyiHXIyCudPqlzALzu XVgJcdP7LtVxhH5mnXTPkwk5KTvluNQfTIwyDOJHH1dNImFiC2vX9rR16RNhRX1TN2/XP3rosXr9Q/pS8nz5eejkPWO70UscR1PKQDmdzY9NQ1Dih9ZCvXzpVT7p4FZm7EM5BNZZSDTsfryW4RGS4H5FfOZUPSwzLyibI36H69lUr/ChP2gtSA0bRgx1sz/a pGla/IlOQQqixV3dIm6ifqxNXbJhbke8n1Nfh3e6pLSpcpPI9qvJZ063m3dGmXFyEeBDqZkiZEUS fjqBELrKH4DdveYM3rpPtfCn1 t1SRd2jJZDvG/VL u3kUO2T7ESMyhGlj72rXhKU5UWWcsTW5cQW72QUPXu F fAuh9l/ysDWIVE6jru2Qf5Xup6axP2h2W WnllB//67SGfyLltCPucwj6nEOL0BKQPcemfKz9k9dP3 yr9g31O58enEwjONrwEgO2uQnw3lBPgvKHRQd4g729jAMQCYgEGgIHdMbB7hd9mQtSP0RYYOD8GQCwYrYABYGB3DOxeIUaT848msBFs9G0M7EAsxaG5ep10QKp2MOo8o4U/pCYBg4PgQ76Uur3PY9cx c6Pz7F nETv wlbPTI/6Jy/rww7X8iwbNaR9o1H1UO7eb3PKY3tGdVxXk9Szu5/Hr9zbTvvh/dgn0SPqJ/1UhyzVrOP9zwvEx d7 Urcco0AafqzGcscnTeyvci9 WIv8ir65FnwnH34rh/39ghPuYTErAc95M6kS FQ0osfDCIG/lW6L7GTDXfTwOfjjzykIDXMs0x9s0908fYzZ5zMRraUTnYTZYD5BSdfCWiMJNYPKNb95kYVPyQCxqL SnovhALt5U5cHL/8VzmlUZnuXR/5fPakSiTS/RSJLtSfQ3PNNoifbxCPhrKVVOJ6G2UD20Y8q3q/waSRL6UW5IOdfrBEcQSup1GiyoQE7N7p0ucuUMcAmwGcCV4r6grc4DefanfOXDmhL18HmpE0zOehGhHnJaeyeQOcuXlVzpnm1gkeFGCNOVaBjNa8smIPtL/whY9/dZIUOuJ7ktwanKN8hdtrizPdtBlcnv4v6md0u4U4KiDXW9JEls2ep2igvHIAHrE1sA4M7EwQHNS2QACqkf33wBhlTQGwOvKrQMrOX4yY9sq44h8zbqRL6Vq9zUYuc z4nwO7MlshZRAQBPG/kVikZHk8d58pnwAAAgnSURBVHQjnPzNhiYZk1R 6xw3AYvpWI18JgIWw3FJp8iX4nGGfClbRv8rlhFicXststQJI6tMT2kU95tc5NQ0w6GpMye2lmeSq0xl21N1qcfVZST21ptzPh8KPS/kUpvKp/lKYh8TEhFC8Fddj9Qdn5d SL9inbpcWE4IGXPdyJcS8ulU89nkm6M 9/GPx6THFc/aPAa1/WkpT8vFqPtYPubpkSWiu8YZoNg1va9Ti1L9r6z l RAzjAU8RLxcdPvbq AK44Gl5YZ VJu4XO36OSlHfEvjHjIl3I7P7tdh0EymL4DA9/HAIjlL8wI0Afg GQYgEFOZhCMpt8fTaHj7 sYxAJiAQaAgd0xsHuFGA2 PxpAx9Dx2TEAYsFoBQwAA7tjgCpMDwBxJGlywGv3Rs/Otl Szx/GWhkygHwvfwN/dJCyPHj5N/pWIWb/BjoVHMjH5ncmljynR0WQLznzWQxn5zsZ1oURMsBhFyvJKmkzrxf5Xv44Fg/xCUmb8FwkujkBHcfh0HHnGOAXjuEH8slnPHOMLwrl0yPT8Ug1xSNRbE 8H18I5kf4eSwfTCI3r8EHyz8pv4a0Py Teg yO9g1Ly9 37R/Zp7SNAYD6306cs59NmORBoydE4C0 0mdyPeCfC Co32vBGgXayHh6 zYOv9HAeg0ypWIhoLshJjoPc15rE5rxvKashfEE9FMPlSdicmRGr1MnmM4Hu5F3Qk5WUoZKv9YHqq/NGXVdRO5pDpJ 18SWkoSrB ZUXxCAoUdfDvcRyHG9/JGvpdkydHEl8QjKZ3RIKCXLL3ybH OYfIxSoSlxzPBFD3j/CTmGRLcuEFHfU/4VwO5PHexa oErICCGDJHKgCezTiUkUQZJrHkThECGX2wH92XmRHJ5R2UjKSdX9opriPlH3rG8l7mOSeWOFuT mP7flYU5BYHj8GKtSBFDVyps3st9F7ajuugPguRWYSrvidg24mk v0Lchvyrel/1Kv0rdO tq/0SctB9wvbkI2ifYo2V5bn/usyIkd2pXZKu38QiZ/VH xwju/FgPpKxoyKTxWXkUzeiQdFPq ZsXQUq4HzFWKhvs6LjlbNgVakkvCjzxCxFfpZ5/QJWAbA657v6DSTKZ hbd6zGZGvSXodbGVyc181PuR IkdfF7m904RY/fKpf2g/Sj 3iEVm 4m9pT/XvJaOVQeWMzrvNaiNXlIEOd6kwshpKZSPmNo5iXjmd1z uKnns75hpoHTJBYjX0qvPN fwrSVNq5pv0WTxqdLoQQs1F51NmHIr0GVOEwELfK9qBkX8r3U/Ujj6JjPjlimJN9ENlsRQcix85kME8u0FOXVngU5FpONTEmLpZKVT4Nk80sLckZu3/1kR xP TciAcizWnb57u2WUEZ5qYtzfEyvhcL69WY1k KTRi4vSyF/dPKERERv/qqXBNUpMfdVy /q1eVizhGdLjHfPH F/a4oj iirJ/tw/tXrn lbO3 9eUr 1Fro5g5ZPqLfcnlyWxDA1cy Fn4Qr4XW6e5jlf/vaKAMWJ UbhTsK ebf31vv6F/iHfywqfHibv1XX2C6Qjkpp2fk oUxAKOZn7uVlmKnqW0NfbX3DSq/RB2ykeV4CNftF UP4vKv80BAodwA92xgAUurNCQRY3mMkCM13e6D4AR4GjAAPAwFoMgFgw gADwMDuGNi9wrXMhucxGgIDfw8DIBaMVsAAMLA7Bnav0Bx96IRtOOD1LmN96Gft9GDT3rL5Q2LVk692W8iHYuvmSg75fXz9DT3tZNODlCFH539tykchCRQTZB2pH9CDdUDQPKY/UCfpI68X VDMwWkn0KP 7/shgT8/8kzxMvogXHZkfH4tTy YHIfnrHNy/J6OvCvB0wN2lcNm/qg9H6lPjmKLY5ZHtu1npUx6daHp/l3UK2csAcw5AUgfPySWanTxFhkt XzOFQ5/GJDVjESX/hbXjn3MfDvxSH0LP3a HmdjwRfNdp SN0djsIuvHv5TLAU8FHrAc0o3ktvEzgdRHGlnoMR4FCYXFT/jggpVfWQAnrG0T65SPbWlkJtp PoqQWaqM9WRiOsVRx1wLLM y3GpTiFVuipdmHUpUFaJRVJFqOe6dRnyrer/Bv307NPLZ9LDT68864XJA/lQuhhZg6fPnqXRpuHwBtC0MxAwYjBgZWpPAlI9rXasRDi1cokDSXCdnwkFB4 zJhnR4v7Oxr2cpN3G6GTozDK61iU/k/S5379QryHfmv4XtvzptJ/I6nWi5aD7wSbaRtE RZsry3P/dRnDIaidcuDq4N oK gc96uD c8PAWeOs49CYYaTaGdoAkMUXwOg3PPXquFr5QZAVPRD2jL6Yz4v5eg63O46sJLjJ8S8VcYR Zp1Ix/KEA40JvDZIhZaCqUjOP0KonOSjCyFEseoAbxGEJlRqsTi872EDGcblkIJWEzHQj6Ueh6exszM2y/BR8U NAhR6tLEDsr2vYGpV57rrWFOtUHPWPjq4d SG983sUE3083ZN/96ovdI0vu0pJHNWTKWLDGYXCobZTryVJ6VFJM8Y pMld2sSjZ9J7dBV93kbXaUCVTar06JWY44RRfg1JYSaU7fTD9TbQYoS4qyfgd6ynXj ljKNt4vqSOVz5XX/ai1UTh45piij/LqBiJum/aXkA/FJNFSd23bXvj563UM TbObTPY59z2OYisrqEEPetBvo3z2Qz2OZ9NDiIQa3YGhfyyASzD4PvhpRgwfEIMwygnNApIBaRydQyAWEAswAAwsC8G/g8bzhKFJRUhDAAAAABJRU5ErkJggg==[/IMG]

---

### Post by TheFu on 2021-08-30
Exactly what do you want to do?

When posting output, please use code tags [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code) and please show the exact command used.

For space issues, the **df** and **du** commands are commonly used.  There are lots and lots of threads in these forums about out of space on the /boot/ partition and addressing that.  Have you seen those? Have you tried those?

---

### Post by Impavidus on 2021-08-30
Which Ubuntu release are you running? 18.04?

And please show us the output of```
dpkg --list | grep linux-
```(In code tags)
That will show the currently installed kernels, header files and kernel metapackages, including flags for any errors.

One can usually cleanly remove kernel packages with dpkg, even when apt no longer works.

---

### Post by HermanAB on 2021-08-30
Well, in principle all you need to do is to look in the grub files to see which kernel file is actually booted and then you can delete the others.

---

### Post by TheFu on 2021-08-30
> **HermanAB said:**
> Well, in principle all you need to do is to look in the grub files to see which kernel file is actually booted and then you can delete the others.

Some installations don't make enough space for the /boot partition, so upgrades fail and we need to be very careful in keeping sufficient free space in /boot/ before attempting any kernel upgrade.  

OTOH, some installations don't create a separate /boot partition at all, so the problem can be completely different.  If /boot is really on the / partition, we need to look for other root causes.

Kernels have 3 parts.  The kernel, the modules and the headers for that specific kernel.  If installation fails along the way for any of those, some manual APT maintenance will be needed.  This seldom happens.  **sudo apt autoremove --purge** should handle any correctly installed, no longer used, packages.  It is the partially installed packages that cause problems and eat storage.

---

### Post by ActionParsnip on 2021-08-30
What is the output of
```

dpkg -l | grep linux-image

```
Thanks

---

### Post by grahammechanical on 2021-08-30
Kernel 4.15.0-155-generic is the newest of the kernels on your machine. So, why do you want to remove 4.15.0-155 and not 4.15.0-148? As previously noted you would need to remove the four parts that make up the kernel. Which are initrd.img, vmlinuz, config and system.map. 

I do not think that the autoremove command will remove kernels that were manually installed by the user. I think that autoremove will remove kernels that are installed through the apt update/upgrade commands.

Every time Software Updater installs a new kernel then the oldest kernel is removed. In this way there will always be two kernels in /boot. 

Regards

---

### Post by rsteinmetz70112 on 2021-08-30
As previously asked why don't you want the most recent kernel?
Before you do anything else you should probably run ```
update-initramfs -u 
```that  should get you updated to the most recent kernel you have which is 4.15.0-155

you can again try ```
apt autoremove
```
It will normally remove all but the last two kernels and update initramfs.

If that doesn't work you can try to remove the older kernels.
```
apt remove *4.15.0-148*
```
If any of the other files related to 4.15.0-148 remain in /boot you can simply remove then 
then ```
update-initramfs -u
```

This has worked for me when I had many old kernels, but be careful and make sure you type everything right.
If that isn't enough space then the only other option I can think of is make /boot bigger.

---

### Post by TheFu on 2021-08-30
> **grahammechanical said:**
> Kernel 4.15.0-155-generic is the newest of the kernels on your machine. So, why do you want to remove 4.15.0-155 and not 4.15.0-148? As previously noted you would need to remove the four parts that make up the kernel. Which are initrd.img, vmlinuz, config and system.map. 

I do not think that the autoremove command will remove kernels that were manually installed by the user. I think that autoremove will remove kernels that are installed through the apt update/upgrade commands.

Every time Software Updater installs a new kernel then the oldest kernel is removed. In this way there will always be two kernels in /boot. 

Regards

My thought process around this was that the 2 newer kernels wouldn't boot, so only the oldest is currently booting.  It was a guess.  If that is true, then the newer kernels aren't properly installed ... which is almost always due to out of space issues on /boot/.  Sometimes the files get left behind, using whatever space is left in /boot/ and the machine's upgrades are all stuck due to that.

Anyway, that was my thinking.  Could be wrong.

---

