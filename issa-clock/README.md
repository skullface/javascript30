# [Issa clock](https://skullface.github.io/issa-clock/)

🕓 Created for my [100 Days of JavaScript](https://github.com/skullface/100-javascript-projects) challenge via [#JavaScript30](https://javascript30.com/)’s second project, [JS and CSS Clock](https://github.com/wesbos/JavaScript30/tree/master/02%20-%20JS%20and%20CSS%20Clock).

## Observations and learnings
#### July 30th, 2017
Holy comments!!!! This one actually made sense to me for the most part! No way I could write it on my own (yet), but I commented the shit out of it as I went to track my understanding of what was actually happening.

One thing that annoyed me as I followed along with the instructor's code was the [repetition in defining the unit of time, converting to degrees, and applying the style](https://github.com/wesbos/JavaScript30/blob/master/02%20-%20JS%20and%20CSS%20Clock/index-FINISHED.html#L80-L90). Converting the unit of time to degrees requires a separate declaration because the math is different for each, but why is it necessary to even define the variable? And adding the `style.transform` for each just to change out the hand div and add the rotate seemed pretty extra. I quickly found [@uuzaix‘s solution](https://github.com/uuzaix/js30/blob/master/02-clock/index.html#L80-L91) to create a `rotateHand` function and forego the variable definition entirely. Score!~

I still really don’t like this CSS… but if you’re going to _build an approximation of an analog clock_ in CSS I guess not everything has to be perfect. 😉

**Bonus points** for my unwieldy “digital” display of the time via `now.getHours() + ':' + now.getMinutes() + ':' now.getSeconds()`. As I was looking into doing some annoying math (00 to 12 is AM, 12 to 12 is PM?!) to display the hours in a 12-hour format and show AM/PM (my function was called `meridiem`, cute!), I discovered `toLocaleString();` to do the whole thing for me. I didn’t expect that part to be so impossibly simple! _Thanks, JavaScript!_

## @TODO
#### Get rid of the ugly glitch when the second hand goes back to "12:00" 🕕

Need some logic to determine if the second & minute hands are at 90 to remove the glitchy jitter of the CSS transform if they are! We'll do this by making the length (in seconds) of the transition 0 so it appears to do nothing (glitches for 0s instead of 0.5s).

```
if rotateHand(handSecond, degree == 90)
  transition is 0s
else
  transition is normal
```
