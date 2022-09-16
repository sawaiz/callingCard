# Calling Card
Card with my information and ideally a place to write a comment.

## PCB
Small circuit board sticks with my information.

## Latex
A system for building complex cards. First side is back and is consistent across all cards, the next 100 pages are the fronts.

Cards are ordered from moo.com and are desigend to fit thier mini cards. I order the luxe versions with green (or perhaps batch1 will be with black) seam.

latexmk -halt-on-error -xelatex

### Images
Install imagemagik

```bash
cd batch#/full
```

Remove any `*.mp4` downloaded by google photos.
```bash
rm *.mp4
```

convert `*.png` to `*.jpg`
```bash
mogrify -format jpg *.png && rm *.png
```

Replace dots with underscores extept extension
```bash
rename 's/\.(?=[^.]*\.)/_/g' *.jpg
```

Rename images to numbers
```bash
ls -1prt | grep -v "/$" | cat -n | while read n f; do mv -n "${f}" "$(printf "%04d" $n).${f#*.}"; done
```

Crop to bleed size aspect ratio in center on longest axis
```bash
mogrify -gravity center -crop 74:32 -path ../ *.*
```