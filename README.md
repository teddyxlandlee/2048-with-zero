This is a modification version of [mevdschee/2048.c](https://github.com/mevdschee/2048.c) which adds
"zero" to the game.

* 0+0=0
* Other numbers can't merge with zero
* Zero cannot be destroyed; they can only be merged
* Merging zeros don't add any score

Add some challenges to the 2048 game!

### Technical details

As in the memory, zero represents "nothing" while 1 represents 2^1=2, 2 represents 2^2=4,
11 represents 2^11=2048, etc., we cannot use 0 to represent the literal "zero".

So we use 255 to represent zero, as it's the max value of `uint8_t` and is big enough and incompletable.

Changes have made at `drawBoard` (to render 255 as `0` instead of 2^255),
`slideArray` (to ensure `255 + 255 = 255`, and not to add 2^255 to the score), as well as
`addRandom` (to make `0` able to be summoned; now `0` has the chance of 1/11 to be summoned each time,
`4` as 1/11 and `2` as 9/11).
