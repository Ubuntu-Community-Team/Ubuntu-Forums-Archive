---
title: "Unable to mount NAS via command line on Ubuntu 24.04"
date: 2024-06-12
forum: General Help
---

### Post by thenewdev on 2024-06-12
Hi All,

Looking for a little bit of help!
I'm attempting to mount an old WD My Live Book Duo network storage drive (FILESRV01) to my Ubuntu server with a mount point of /mnt/nas but can't seem to get it to work.

Attempted:
```

sudo mount -t cifs //FILESRV01.local/data /mnt/nas
sudo mount -t cifs //FILESRV01.local/data /mnt/nas -o username=XXXX
sudo mount -t cifs //FILESRV01.local/data /mnt/nas -o username=XXXX,domain=WORKGROUP
sudo mount -t cifs //192.168.X.X/data /mnt/nas
sudo mount -t cifs //192.168.X.X/data /mnt/nas -o username=XXXX
sudo mount -t cifs //192.168.X.X/data /mnt/nas -o username=XXXX,domain=WORKGROUP
sudo mount -t cifs //192.168.X.X/data /mnt/nas -o username=WORKGROUP/XXXX


```

Alongside every other variant including gid, uid, etc...
Also attempted mounting via ```
[COLOR=#444444][FONT=Consolas]smbclient -L[/FONT][/COLOR]
```
All of which return mount error(22): Invalid argument

Checking dmesg displays: ```
CIFS: VFS: cifs_mount failed w/return code = -22
```
-
In troubleshooting, I went ahead and installed Ubuntu Desktop to use the GUI - which sees and mounts the drive just fine without any additional work.
 [IMG]https://imgur.com/a/XMe3rQ9[/IMG]
[IMG]https://imgur.com/a/XMe3rQ9[/IMG]
[https://imgur.com/a/XMe3rQ9](https://imgur.com/a/XMe3rQ9)

But even after confirming that it could mount via the GUI - attempting to mount via command line on the Desktop version still gives return code -22

Via ```
smbclient -L
``` the server confirms that it can see the shares and does list them
[https://imgur.com/QR0u9Qz](https://imgur.com/QR0u9Qz)
[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAaAAAADLCAYAAAAockd0AAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAADsMAAA7DAcdvqGQAACKZSURBVHhe7d2/burK2gbwZ393cPolWShL2pKrXIFFgZTO7JqGgibFERIlDYVPQYlElYaChvpAh0TB5gpSuUqE3J972N879hhsY2wTkwwhz09irRjjP9iv/c6MzfiPX79 /QMiIqIv9n/6fyIioi/FBEREREYwARERkRFMQEREZAQTEBERGcEERERERjABERGREUxARERkBBMQEREZwQR0CXuA5esUrh4kIqKPYwIiIiIjmICybBfT5RKvr6/Rayk1HluPo7vmTvU z3ktBwyCquzBFMt428nx8 02nTuVdWdLx1dgAkqR5LPwgNkQj4 P0Wu4wcPzAJ9zDNmwbXnpITJr1df7XF6jHRDMO4fh9sTXn6Ii9mCJRVMOoc7x Gk88VRO ZiAkuwHWNhhs0qcbPwVJv0JUqcfKSElS3ipGpLUoAbTYw1qOc0mL0lyUroayIG6fB1jPB5jkSpt2TL75PTucfr4GtRHlx9Ov8Q0HC//D9Sw lyylFqw/B9P7btXyCZJsDFY6vf0/hkkagCn2et6 L5y4wH/ZxOITk OlPVnpAke1VGN8F8Vk3fsuOn3C8vOc5MuDAiz8T7lz6DExASf47Agm8nmo2kKg8BG6KjG9tMAxLxh2MAgnU52OAuk8tYBPXoDrYoovFSQA7aDZmMo822u02HjsviA9Rd7qAhxk68fSWh3GqDaP 8vcvbXTmMqduAzP53Ggn6/MULaN8 T/ZCi9ziZBWYnu6z haqtCih2X/dBt6/3RGJ9vvrrdvWIAL8F5QWVTfvxt//5ztoxTFp1IvfguOH3 CtnpfVX lIDoKPyOvfjKB0jUxAaVIaU0OikAOo663kJqJLiHpsZEA25eVrhH5WG0kWK2HQ7JaTfqYHIt/mGTGR5LzEH78l4uWE2CemP9ktoPVfEpMX3f50QnCfw/kzz3e9LuRKsv/2fz1FoHTOsSE25LS8m5zKECo7XvYfqr2nNp P337Zr7/yfZRiuJTqRu/xccPfS0moCzVZKBqJbqENFclpFQNoriEB1eq8UtddT9U5ysKS5CS/BZF05te/g/nr7GVmOiFperjCe oYP/89O1boYZUyzWOH/pSTECF8moQRVxMvS6C2fHidVSdryhsAkxU/eNXO3MN6izTy/8JEqVqtwUn2GKd2jgWHs4Fy71v3/D7lX3/gvF1MX6/HSagJHuAqbpoeThAbAxUE0vwfkEAB9jHn1Y3BPQuKeGusNlFNa54FWyp0UwH6UbAYqaX/wOsNthZXSykdB1s15nYkBL4s95 evsfP3Pv21ddIwO64 SFfSkUHb6f v5F26euK23ft/3nJko6YAJK8id42bQwHsdV AWamKNT SJkdJG66enpxy28by ogYhVv4MRetH1J3nJLLBZf5fl/xTqRKf 32F2cnv2DvO9xJDafgsPzWCEYeIz9759/UkbnS3Qi5vB5AvuE99Pff95/P1ztk9dV9m ch6QSu6xKU8SGn2OP379 vWP/puIKgp/79KYpe QUrfxLtSdWX1JUURUhjUgooup37tY2B3vvSaiD2ACIrpA1F2PB2s3An8eQlQPm CIiMgI1oCIiMgIJiAiIjKCCYiIiIxgAiIiIiOYgIiIyAgmICIiMoIJiIiIjODvgE78hT// x/8Sw8Bf Ptr3/jf3qI4 8dt289prffZ4 na2ICIiIiI9gER0RERjABERGREUxARERkBBMQEREZwQRERERGMAEREZERTEBERFdnw3Vt ZeKMAGZYg8wXU7h6kEiuiP2E3reM37rwa9mD6ZYDkylP0m 0yUGFU5uTEApNgZL9cjl9OuwI91pZtxSxp1u5XDnx5 RJJMXB/bvBizLwoPNMtLt Lr9f59uYPvZrhTslsdlqEKeie3vT9B 7MPMU9tdPHctbNe Htb09k8lJvXecpCpqen9ePK qLR9faw2Abq9nOkzmIBSfEzaj3h87GAeAMG8I38/oj1J7sgdRvKeev xM0PQ9VI71B4ssWgCs47 zHCDxlPyIJMdKDtu3JI/ZRmN5zGW0wpFBfoCX7H/75np7SfH1sKTiYfRtHr6h fyE2E G7YUEJPT5pYXb6wQaQ96cHYzpDZ7gtV9Lm55kdpb0woQWE08pb7aBdt39YI5ungu2XVMQHX4K7zIkWY14oq2KnkA86GUfOKdL5/pT47loCg4Rmj3NwiCGfr9tvxtppxENX1g/1PCtbef/QBLEtzmMLGQ6Sf9iaTGWNQ8FJfgVeEvffJUBUSpdUkiXL6OMR6PsZDh8DxqDzBeZJrN5b3lInlCjwqY0fzzmtizyz tfRSvXxkbT03ZCptz22yH3c5Br6BaaT81YUkCm 0sNJMZqNL2jflYbwM4reIMxAR0TeEOCvB ujfSrIcLg4q har7n/LV3X7 u0wtJ1fVbHfmBgB3uoCHGTphCb6DreVhfHIydtBszDB8lMJhuy01tZeoKc1fYxs4SJ5To5P1JtHUJgkznPdITtWnwuVbW4x0DU8qEEhW8KqtX5HfaFgB9m96MMfmZQ7JLGfOQccEttrsYCU/V2H7JvnvUg0uOdcxAdVhR22tQdHezvAnQ8yDppSqPDhOD9OBlHAuiS 6HR/Y/5Rw9e0nJ//OSE6SFrreQo4xqUWoaxR6rKqdtJwA85eVLrH7mMwyJ9lQgO3hM8KP/8qW6qP1P1/byNLLH04ONTx/NcGxgld1/QqESbyESqTnmsfC5jdVy5G/VxvsUs1wZds3h9UovBGDCehiDjxdPX5d9GDNR5k27jISVH0pVakSUrDFvtHDIlutpxtWd///dJ 8/VSTnaq16BrEXGosXnyNNTw5y8lzoZevXp4TjavIn8ywk4JjWClxW3CCOSRfVFNWw7vC lUTJTYn5yaBsEYX7BEVCd6wDzLNcEXb9wOYgC6WuIiqqujJ9umwiqrubNPDZYJ3SUaqRpSu1tMtu L /5G cvvJiXazOzYDhfNPLl /2nnXMM5ZYaOvjbgtB8F2XX3asu93jfUL51FBfJOAuhkq4XdD6k9WN6rdvC4gFbzENbqszPbNc0hm ZiArkpdVAW6Y6nRxHtE3baYuNXUdt30bYt2eZstfRfl 5 K1Nx 6rd16qL94fiyMZAkoQp60QlcJY oxH6cvUxz4f6Jro08h81lJ7c6p2STTZS8uuPB4fup5R8Xf431OybIYro50UnWsHQTYHwHonqNJME4raiFpnT7plVJ0ExAKfHvGHTm7y7CanDqvvkS/qSNzhboxdXocQv79bGU5 MBrbG6y0VdA/LCZgiMhmdvmaSv9Pn7/74Z3n7 BC bFsZjPa2sR1PK Z3EXaarfgcj9HQJP/o5xObS/RNeG3HgBFuczz8r9EcBmvp7xNsgXH7QhKffV8tPLv4a63dy88AZYXOi/jukmhSl/pRqIlTfVd4NW2gqbN jKJkVJ2g EdWc8PbNBmbGfqxGRPdJFQTGwLBtrmCrfuDa26NT0nzIGhAR0V1RNxlI7cvYD6BV05wV3u1Xlv9YAyIiIiNYAyIiIiOYgMrkdtZHZF/e3b667ve6/EGdkxIVYwIi gjD3e0T3QMmoM8QdnvO3g2 Hd1dffxa5nY1rxntbp/oPjABEaUcf4k nKnfo7DJjOizMAGdcDE9PFRLTj4P u2Y7WJwrjv1sI1f3g/7b0r0eZXsK6loerop/qqPofplfqrXxuLu9m2pRR0epibxMz1bhVLhouKgoJZFdOeYgDLcqQcnGEXdoXekCNxMdwboPqmfJscPZOqEvcou4gQTNsvo7iuSfTolfilcOD3dnNMu5VcF3e27ePYsbEd6vz8OsWk95TbFquQzbgYSI4ln3xD9MExAKZnu0NXDlmbp08xq0sfk LSs8s74MupOT7fOQvMh7i/Lx6o/OblO1HheYtENMGvzGhL9bExASVUeiOUOsDw00cnr0u7S605PN0w9L2WOoNnDOOzra4npyQUkC44VSJSxB3QiJqCk0u7gXUy9LoJZ9Kz78BU2t1VVd3r6avaDdba331z JHxeimqK7YwkzZw8f189kKyPtux3x MNDvSzMQGl6O7Sn3V36OqGgV62hhJgH5 OcseLt31BIqswPd0EdUPBuIuwSTZfZh r7uoHx670C636GOmu ZmD6KdiAspQ3aHPLS/qDl09KmGbrKGo55UEaHq6 WzcwntqvCalYHXp6PBkw8NNBhWnJ4OOdy OZffPOud6FM7pbl91V48Wxnp6FT7zzvnrPGGsoXvhM/ J7gc7IyUiIiNYAyIiIiOYgIiIyAgmICIiMoIJ6JrCrnjOd0Iadb2ib0Ao7az0A9390xfi4xiu7rsfPyXrT6eYgL6QP2lHv/1RP1bU753F7v5vG/fPl Pxc3 YgJIy3fGrX7IvB4bKM zu/ vxcQz1/ITjx1adFSdqYkUxQqWYgE4kOhHtzBB0veg3HvRD8HEM9dzz8SPJZ EBs7gzYXkNN3h4/qwfE9uw7ftuhmcCKuJHPxy1Groin9fGq0p9mUd2PwyOXfIvpxV/GX9Q3N2/CkqXj3P4EnwcQ033dvyEfUXusEl2X646LO5P0l01JWMgW0MqfRyLWv8pBhIby9cxxuMxFqnvkV3/S7fPbWECujoH3cYGw7AEOMLW8i78pXtRd/8qthfwrC1GnagEJgUwPJ0eZXQlfBzDV7vh4yfsK9JBT5LKQLJK/lrJ JZe/8cORoEDL1GAqfY4FgfNxkzm0Ua73Zbt8HJoSgzXH7PocTFq ou3z21hAioipZXnroVg/6bfqOL0cQ5W8 lKpRT9uIjh5HDS8lcTTHgh4obwcQwHd3f8qN7OR7KGFrreIuquS9Vw9NhIgG28/mr/Zx63Uu1xLMl5CD/ K/O4GDX9VbfP12MCOpF4kumiB2s Qju/M7AzSh7nUEeVx0WQQeoE9dMfx3Dnx48kRdXbeVyDmasaTqoG84mPcwnXX5Jf3MfkpdPfICagE4mLqKoKfHH1ouhxDjWVPi6Cro2PY7jUTzp Ln2gpFvvcSzh ie3r361M9egvhEmoEvEbcDxWSP3cQqnj3MItut0gOj5lJeAsweLflzEeHC4sGlLicrUna73jo9juLLvfvyo/asu h/maWPQkvW/pIAia/7xx7Go9Y9qXPEqqPVXMfddMQFdRKrfqsTSXUTV39zHKeww3 su RcemkFeE0Q0H0s/liH/NlX1mUx3/ rdvrqw2YSn35dVwPquLyR8tWMTEh/HcG3f/PhR 3cj6zaOpn19XaApe7DTrzqD o9jCdcfvej6k17/zTc AfBxDEREZARrQEREZAQTEBERGcEERERERjABfZiB7t4v8oH1 0ndyas7muLfY2S6gvm2wv13v33X3dbjGG79 P8emIA 6ta7e7/37uhtt9YJwH3uwtrq32N8499R/CQ39TgGPu7hKtIJSHUMeChhqJfB7tRNCrdDSQnr1rvjL1q/Kt/voyQxnO2uPo6v5C/Hw1K7 pzUQk7i7/VMZ4uyjIUH78MnABvR70uZdu5WnePzHo7/byKnBnTP3anT54oSQ3F39QECq3U4uO2npryVLM8mf md19mijcHSg7XbySdNkxqY0e7yP3v5pr8f3bviJrhsd qhsu7As Oz7etyAjk3fXwNQkogud2Zl40P1Vi/uDQe9q U6NMqWWJXJ9n4/WwpqeL6DQ59QS0xGEhpq9I1iGi61KpoYdv4YUTZ sn7hd9PFK5/gUrd1QfYbi39a3jVWaUajsac8rHeZuNPbEdo9zd64BLxtl gKzUgJ/5BYGr7F8RnSG3fou7yz6m6/663/PzHPcTbQL3y4q9s/gXrF8e/Hgyp2kQ8fz1eLTOOr9PvV1dB/IvCx2Xc9PF/n4oTkC0niKacUjbHimZZd Bl3Z2r8d14 tzu1ou7My8bX2v9wmq1vB/2z5Qoiad 6bwq7O69yvp1g5H /jOgWbUrDh/RkwFOQ/V3I9njcMH6Vfp Zdu/QNzVihx057urB97XknFUD75uC85ug7V /4TE35PEX7o3ZR TD3f/LdO2o 8l5Srs4scmJK4Blcencr67/POq7b9rLf/c4x6qxV/x4wDK169I3cctlCk6Pksel3HTx/99yklAssHi7K36Epl1cNz Zd2Bl3V3npk t7v14u7Mi8fXXb9ruGD99PevSs0rrg24Uyk9hgeuup4hy1zrL1Rb2fYvIgennFSKu6sX/hpbNDHuOanCTSQZf1FXLMOLelOuo0p8KsltJA7d5Rcr33/XWf75xz1Ujb9z86 6fkXqTl9X eMy6ik6fuod//eo8BpQZy6nAy/Rm29Zd Bl3Z1X6g69xvi663cVdb9/gbc9AkddP5FAtqQ4rQ5c wlN ft636nmvOSgKu6uXlEFA0lTlmqu028dpK8BzaQ e/rArk/y2fFRtv usvyCxz3Unf9V1u8Tt28pVUAqe1xGXQXf77Pj6xsqbILzJ8PwBHLovTZsYkmeIPQrbsIIxxd0d142vq666/fZ6i4/nn7QgrUdYhY08fTUgLXbXLkUdy2SaM7VoFZ92TdldxHpEmR40v4CXxKfBfvvKsuXEva5xz1cK/5qrd8nbt8q/LLHZXyiz46vb6j4GlBYUpUq8mEnlXUHXtbduR7/rKfX3ZGfdLf YXXXT1Ml1UqBcmkw5X//6qLpm00rbLJZbYLw7/NPnDyzfpW/34Xsa3RXn2TDDe X3uOSZ2p 3FfEZ9H u Lycx/3cJ34O7t 4Qk2UWDNnf8Vvp9ezsWPY1DxKQd78q1cxo9/N/qRdOI8dq9KEpBYbaROcQyqsu7Ay7o7j7qg19N/Qht/3fULSSlJNc0emvJym4CkOp/T3XuZ8PtbXrR auEXdsf tpdDw9LVeDlQZODM71kK1q/S9/sAmW 97uqVxDUgmb7X3GI0TN5FF9 F5Mkn48/mXGf6oM Oz7L9d83lR/NKP 6hbvwVr5 KuTCwov0n86/yuIXLv1 0nIsfx6Dis8rjMm7h Jdyl2o5uHd8HINp6jbV3h4d/hqfTPjK FO3KS8amPEHnEdnt79KaPd/RiivAdF1qSbBww8D7I81QRB9FOPPrMrb/2fsESagr7ZaY9MaR1V71UR15SYeokKMP7O4/VPYBEdEREawBkREREYwARERkRFMQEREZAQTEBERGcEERERERjABERGREUxARERkBBMQEREZwQRERERGMAEREZERTEBERGQEExARERnBBEREREYwARERkRFMQEREZAQTEBERGcEERERERjABZdkupsulfmSuvJZTHB7hTnQD7MEUy0R8Dr5bfLpTWXc5rvQg/VxMQCmSfBYeMBvi8fExeg03eHge4GPHuA3blpceUmTwVO6bVZzOn 6bPVhi0ZQQ7Rzjs/HEUzl9T3/8 vXrH/032QMsFw3MHvtY6bdO2VKAG8NzrHAo2I0w7K/gh0OKJLHXFvZzC82uDAaAZQUYqXnmzf/kvRrzjz5Ad0vt x72nTYmx4DIsDGQ OnmxU8Ya015D3AcYDffwup2YWGHeaePCUrGRzM5H59xLI AnufIdOEHMBpKbKoPhOPV/DJkHo8yD/p5WANK8t/lfO6gp5o13PyahTtdwMMMnbCG1MHW8jA aQNx0GzMMHxso91u47HzEiUHf41t4KCVKLDaT01Yu80hedSaP903 0FO3gHezyafKH66cfx0Rrnxs39pozOXKOqqgs8jRjuJp6fjZ4rGl8enHD tjcRmNH4k8e4964D3J2ir90eS4SSpjcLPyIvJ58diAkpZoS8HbSCHeddbYBFfA9JjVQm05QSYv8Q1Eh T2Q5W8ymTrAJsD58RfvyXj/VWUtwhA7l47kr5cnNIPzXnTz9bJn78VU78RAnMf5eqc7DHm373qGh8lfhMxqaP1UaSjfWQW5gjYgLKkoO2r2oVugQ3VyW4qU4YYQlUktNCXwBWL8 JxlXkT2bYOb3owrHbghPMIcdr5Arzpx sQg2plkrx YnLp7vDBFRISnjJElzYRJdoOohf7Yku8VWxwmZnhU0abstBsF0fp73K/OluhfFh4eFcdaJsfF2MT7oyJqAke4Cp1HaON6XZGEiSQPCuDzCVPKIaUfwR25VpBomLOhWoZgmr Rw2Z2zXyUP3OvOne7XCyxzojhM/DVA/GzjER1S46T7r JFxg16mkFPLleLzbf 5iZK DSagJH Cl00L43HcxLBAE3N0EhdJV/0ORuhF14fkNW4Bm/WFF1FXG wsB06wRSr/iKvMn 6WP2mjswV6cTOYBMg ER8qfuZx/Cw8NIMRhudvmbvYVeJTjrPZThJp/B3iJm76cXgbNhERGcEaEBERGcEERERERjABERGREUxARERkBBMQEREZwQRERERGMAEREZERTEBERGQEExARERnBBEREREawK54Tf HP//4H/9JDwN94vf J8e4ngy69bjo 54 kmYgIiIyAg2wRERkRFMQEREZAQTEBERGcEERERERjABERGREUxARERkBBMQEREZwQRERERGMAEREZERTEBERGQEExARERnBBEREREYwARERkRFMQEREZAQTEBERGcEERERERjABERGREUxARERkBBMQEREZwQRERERGMAEREZERTEBfyR5g brEwNbDREQ/GBMQEREZwQR04GL6 oqpqwcT7MESr3kjiL6SO8WrxGgqFsNatby3HOBqFetwOVM5Iog FxPQwRv2AWA9nB7GvxsWgv2bHrqEDduWlx66vs eP92eAIHVOiQH 6kpb0ng3iTGJxVjAjrw8Z57HNt4sPSfIRuDqdSIVKlTXkspjaYPMFWTmmIgtabl6xjj8RiLM6XJsGalxqVmIPNfRvN VdeLBlIaTZVuy ZfsH5haTmzLqq0G89fj1fLDEvVud PzAqw3VrohRcSXTx31XA0JmS7mf2frhnZsr/jfavia5oMvrg25Tky4MCLP5eq/dsSMteJfyImoIQ3qQJZjd/yV9Qclzzwgnc//N dLtDFDJ3HRzx2RthaHsYndxU4aDZmGD620W635XMvWOkxMZV8xs0Ao8c VtGsQ H8g5Ge/wxoqpNB1vn5V1u/Ig66jY3M 6PT02d7X0vGaT5JMmnB2W2w1u8r7lML2AzxqPbfYwdbiYbFIY4lYXkWtiM1Tr2G2LSejsnBn6Ct3h/tZGAnsak/1z9Gr4ovL44vNf8Pxj RwgSU4KsqkPUA236AFQQIHNXU8RsNK0DUAuei5QSYv6ykvqQmWGEy28FSJwM1fCCl0vgzip/IMKLxvMRCSq6ztiQf/V4kf/6nzs2/6voVqTs9fTp/LYmliXHPwW6TjqDVpI/JoUTjY7KR FExrd RATQfpNYSvuFj1Z9ckBwy8aXm/4H4J4oxASW97RFYDTypdvXtDLOdhQdXkpEcUGEFSCWm O8Ps BYktyklNjKtkvUnf9V1q/u9PT51IlfauvWDpn8IzligOWhCVdeYXNabIV Z46g2cN4ocYvMb2kdhvGl4VuOG3e/IkuwwSU5L/L6VdqKOqmg/eVykdo9ppSG9ojrACF4yUp1aoOSAly2Ed7tIPjZX4TVHf V1m/utPTl1j18aiab/VgxMXU6yKYdXQTW9ycluBP0G 3w6a2zkiKQd1nmaqiML4STXPxqz051naILsAElKLuhHPgOFHJ0ldt7ZYlOeNdH2ArbKRW1H3WF17VBd eg2C7vvwAlBPISM1rnLxInD//6krWLzyBOPoCtsid/5W HxkSYB/vrez tQdS49H7tohqCcgtiKj4cuAlbjywpcal5kn0EUxAKfpOuFSNRw0eb8Fe9TuYo4eFan5YeGgGIwwnHzs9R/Pqpi7ihu9ZXjT/cQvY5l0DOq94/VboqxJxdxE1n8j830/mv8N838L4Ct PvtoKL/MATU/2Xd7 ldrPC/S ldeiB8w72VqUkM pS4 HprbEzTgqvkZxfMlLhehmXf0qElHSH79 /fpH/023SN0m3duj8xXNHOo23EUDs5OmHSKi62MN6NaoJo3DbzNsNoER0d1iAro1qzU2rXHU9PG6YBMYEd0tNsEREZERrAEREZERTEBERGQEExARERnBBEREREYwARERkRFMQEREZAQTEBERGcHfAZ34C3/ 9z/4lx4C/sbbX//G//QQx5NZtx4fdcfTT8IERERERrAJjoiIjGACIiIiI5iAiIjICCYgIiIyggmIiIiMYAIiIiIjmICIiMgIJiAi n5sF65rI354PX1PTEAHLqavr5i6ejDBHizxehhhYzCV4fCR2a9YyvuHg8CdHt6PXkssB4kZ2gMsX6eypKNw3svMezKfZTwPGTeIF1A2/1DZ uUsP/5uleZPRp3so2g/RTEi 36ZHScxEAdQTvyl5M47c0zIiX 6PMZXGLtV4zNcfryuR 5UPpt7fC0xzX44JOuw8OB5z/it36HviQno4A37ALAeTgP d8NCsH8L/3anC3QxQ fxEY PHWwtD PUQbLDKBwnr84MQdc7ngAy1Ml/0QwwavexSr7XA2YdPY/hBngeHJNIyfzL169M9fUnQ4K53r/xq42Jr0b4mLTVcAdzieVg3gnHt6ORFSX2v3714 DUJ37MhsfxEp8PVePTX2MbWGg JePJRcuRqTbRQqL43UbfT6ZHd5EpFKok68Ha7WRJ9N0xAR34eJeD9pSNB0v/GR4sAeYvK/m0Igf8bAer ZQ4ABP8FV7kTGA1TstpeclHzf 5C8yH8l58zpB5TPoTvbyMk/lfuH5lCtaffiD7AZac9jeH4BQXxaeP9VaGk/HotuCE8wwHdPzq enpnVamzrYdod2Xghl9e0xACW9SBYoOlqg57tgsIKXJdzkkwgMwgPrz4G2PwGrkNwXYklCacsjq0l3sQSWfbjb5iLz5F8nO/9L1I7qE/y7R5aCnmoWrXH/JiX9/vU3Fo61Kd7tNdBzkxK vSoXWQ2JZUqiapI8n r6YgBIOwa4OhCBA4LQkFf1GwwqgW AqcODFbeBRW1qiCUNx0G1KQpP/swW7rPD6jG4LP7aClc3/itQJpHtsfqQbYXWxiGNAvdJtVDUl4it8JWNvhX5nJLFroestonXIXL8sjc wGS6OfRtPOQU09b66lnVoumMB6m4xASXp2sLTk2SI7QyznYUH98JaSaINvDOXw9F7zhygMr7dRnu0k3GnF2ST/Elb5jPKtHWXzb A n76z/PSJxBrPrrwGgJ9uuw1oKuWQLLXgOLrS5ovSUjiNxqnrjVJvKQSYFl8Rs1wYbOa/YSmFTe/JUXXsg5xF zBItB9YgJKCpsYgIa66eB9pc7XaPaaUhvSB0A4XpJSMmn8bhzHZ/iTYXiA9vKyzKqPkSS47jhxATdv/gVO5n/h uVLnoAkUbK5g86SRLGR4lGqiezoXPzHLQ1uNjZz4jdsogveo2tCdHeYgFLUnXAOHCcqlan2aljJA2CFjUoaz/GtzTYGPQfBdn3mANE3AXTzaymrvtRurG7iLjV10RWSlBK3ttoP o882fmXrF94gKvmDz1z2w2bQNjERpXYA0yltmPHsaniS93CdjZBnIn/1UbivoneybETx68ulOkm4NMmOroXTEAp k64VI1HDR5P0Kt B3P0dBv8As1ghGFRE5U62OSkn1sLUm3qI3WAjg9NcarZrSN5r7eIm8GawHyG9blFZOZfvH6qDV8yXG h5 2Vrz99I9G1E7Xf5bwtcRXt5/Rt9NlrPPJKNaGdjj/eRj3By6aF8TgeJ/El0dYpagLMjf8o0VhWgG0msKP4bUbxq64hzbPXOPUNQq ezDVe14LfNtFN4xNRiYjICNaAiIjIAOD/AXzON0bwKKpeAAAAAElFTkSuQmCC[/IMG]

I've tried every other mount option I could find out there and still nothing.
Any guidance is really appreciated, thanks!

---

### Post by Morbius1 on 2024-06-13
Most of the time an "invalid option" error usually indicates the client is trying to access the server with a smb dialect the server doesn't understand.

By default mount.cifs will try to access the server with smb dialects between 2.1 and 3.11. If the server is that old it may not unserstand anything in that range.

You can override the cifs defaults by using the vers= option.


sudo mount -t cifs //FILESRV01.local/data /mnt/nas -o username=XXXX,vers=2.0

Or 

sudo mount -t cifs //FILESRV01.local/data /mnt/nas -o username=XXXX,vers=1.0

---

### Post by thenewdev on 2024-06-13
Morbius - thank you SO much. That did it!
This one resolved my issue - 
```
[COLOR=#000000]sudo mount -t cifs //FILESRV01.local/data /mnt/nas -o username=XXXX,vers=1.0[/COLOR]
```

I really appreciate your help.

---

### Post by TheFu on 2024-06-13
ver 1 is terribly non-secure.   If you want to KNOW which protocols your NAS will support, use the nmap tool:
```
$ sudo nmap --script smb-protocols    _win7ult_
Starting Nmap 7.80 ( https://nmap.org ) at 2024-06-13 09:46 EDT
Nmap scan report for win7ult (172.22.22.8)
Host is up (0.00078s latency).
Not shown: 995 filtered ports
PORT      STATE SERVICE
135/tcp   open  msrpc
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
5357/tcp  open  wsdapi
49156/tcp open  unknown
MAC Address: 52:54:00:7B:8A:14 (QEMU virtual NIC)

Host script results:
| smb-protocols: 
|   dialects: 
|     NT LM 0.12 (SMBv1) [dangerous, but default]
|     2.02
|_    2.10

Nmap done: 1 IP address (1 host up) scanned in 11.84 seconds

```
Just replace the underlined part with the IP address of your NAS.  I have DNS running here, so the IP lookup happens that way, but a normal IP address can be used too.

When I connect to that CIFS share, I use **vers=2.1**. It is the highest, supported, value.  Win10+ should be using version 3+ which are drastically more secure than prior versions.  There's only so much we can do.  Any NAS that only supports v1 really is ready to be retired.  Something to work into your plans.

---

### Post by thenewdev on 2024-06-14
Thanks for this! My NAS didn't support 2.1, but it did have Version 2 and so I switched commands to

```
[COLOR=#000000][FONT=&amp]sudo mount -t cifs //FILESRV01.local/data /mnt/nas -o username=XXXX,vers=2.0
```
instead.

Thanks! [/FONT][/COLOR]

---

### Post by aoakley on 2024-09-26
Hi, jotting this down here as it's a top hit for "ubuntu 24.04 cifs mount bad option". I encountered this error after upgrading from Ubuntu 22.04 to 24.04 . dmesg shows "bad value for password". It was caused by the password option being blank. The solution is simply to omit the password option.

This /etc/fstab entry was valid in 22.04:

//192.168.0.249/FamilyLibrary  /mnt/bigpenguin  cifs  x-systemd.automount,auto,nofail,nounix,username=guest,password=,uid=nobody,gid=sambashare,file_mode=0660,dir_mode=0770  0  0

(note ,password=, )

...but it had to be changed to the following to work in 24.04:

//192.168.0.249/FamilyLibrary  /mnt/bigpenguin  cifs  x-systemd.automount,auto,nofail,nounix,username=guest,uid=nobody,gid=sambashare,file_mode=0660,dir_mode=0770  0  0

---

