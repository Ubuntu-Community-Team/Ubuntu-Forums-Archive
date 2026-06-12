---
title: "Rename multiple unicode file to ascii"
date: 2017-05-06
forum: General Help
---

### Post by feing on 2017-05-06
Hello all,

I have multiple files name in vietnamese, i wanted to rename it into ascii i.e.

Dán n&#7897;i dung Ti&#7871;ng Vi&#7879;t c&#7847;n xóa vào &#273;ây  >>>>> Dan noi dung Tieng Viet can xoa vao day

i need to do this using terminal

i've tried 

rename y/  but the result isn't the same like i want in the above example.

can someone point me to the right direction.

thanks

---

### Post by frostschutz on 2017-05-06
iconv can do the transliterating part

```

$ echo Dán n&#7897;i dung Ti&#7871;ng Vi&#7879;t c&#7847;n xóa vào &#273;ây | iconv -f UTF-8 -t ASCII//TRANSLIT
Dan noi dung Tieng Viet can xoa vao day

```

in a for loop that could be

```

for file in *
do
    conv=$(echo -n "$file" | iconv -f UTF-8 -t ASCII//TRANSLIT)
    [ "$conv" != "$file" ] && mv -v -b -i "$file" "$conv"
done

```

output by mv

```

'Dán n&#7897;i dung Ti&#7871;ng Vi&#7879;t c&#7847;n xóa vào &#273;ây' -> 'Dan noi dung Tieng Viet can xoa vao day'

```

The problem is how to treat homophones (if such things are common).

---

### Post by feing on 2017-05-06
thank you frostschutz, it work great so far.

---

