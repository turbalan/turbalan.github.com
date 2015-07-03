---
title: Naming Conventions
permalink: /naming-conventions/
---
#{{page.title}} &amp; BEM
{:.no_toc}

+ ToC
{:toc}
{: .toc}

##Abstract
So, how exactly do we pick the names of our blocks of elements? It's one of the oldest problems in programming altogether. True for [CSS], especially. There are a lot of articles on the web dealing with the matter. Here we will try to outline general rules, and leave the desicions to the developer.

###Choosing the name
One of the trickiest things with CSS might as well be how to name that class...

Do you use [BEM], is it a block, is it an element from a block? Is it reusable? Lots of questions that go into a simple `.phone` class.

I don't want to give advice on this, just go and read Harry Robert's [css guidelines].

##.red or .warning
Some people say that it's really bad to use words such as `red`, `green` in your classnames and you should use words like `warning` or `success`. I actually don't get that. I see no problem in having a `.btn--red` class for a red button. I don't exactly feel the danger when clicking on some red buttons, or it's not a button for a successful action, when the button is green. In my mind `.btn-danger` is more vague than `.btn-red`. Anyway we can always use both:

~~~
.btn--danger,
.btn--red {
  background-color: $c-danger;
}
~~~

A thing to note, the colors for buttons with classes like colours can never change. They are **immutable classes**. From the above example if we have to change the danger button from a really red colour to a more orange one we would do:

~~~
.btn--red {
  background-color: $c-danger;
}

.btn--danger {
  background-color: $c-sunburn;
}
~~~

##Hyphen Delimited
Before [BEM], developers were using `-`, `_` or `camelCase` to "semantically" name their classes. The only reasonable character or technique to use is hyphen delimited words.

~~~
.nav {
  width: 100%;
  height: 40px;
  position: fixed;
  top: 0;
}

.nav-link {
  display: block;
}
~~~

If we are working on a smaller project, that will not change, or not change much, we don't need to use [BEM]-like naming conventions. We have good code only using `-`. With reasonable choices for classnames it's enought to transcend the meaning and connection between modules and elements.

##BEM

For more complicated stuff we should use [BEM].
Again Harry's explanation about it is verry good and you can read about it [here on csswizardry] and [at the cssguidelin.es]. We will use his 'style'.

Let's give an example:

We have this HTML structure:

~~~
<div class="interview-strength">
  <h4 class="interview-strength__header">
    <i class="fa fa-signal"></i> Signal strength
  </h4>

  <ul class="strength">
    <li class="strength-column">
      <span class="strength-column__progress"></span>
      <i class="fa fa-square"></i>
    </li>
    <li class="strength-column">
      <span class="strength-column__progress"></span>
      <i class="icon icon-goal"></i>
    </li>
    <li class="strength-column">
      <span class="strength-column__progress"></span>
      <i class="fa fa-check"></i>
    </li>
    <li class="strength-column">
      <span class="strength-column__progress"></span>
      <span class="strentgth-column__hash">#</span>
    </li>
  </ul>

  <div class="opportunity-graph">
    <span class="opportunity-column" style="width: 43%"></span>
    <p>there's an opportunity here</p>
  </div>
</div>
~~~

The code is from [Signal.ly], the signal strength graph on the right.

Some things to note:

+ We don't continue putting `interview-strength` in our classes below the header. There is no need as the blocks inside are autonomous.
+ `strength-column`, and not `strength__column`, because I see it as a block, containing elements
+ `fa` and `icon` don't have classes like `interview-strength__icon`. No need for that

This is where the confusion comes when talking about BEM. Do I continue to use the name of the module? Do I choose a new classname and continue on from there? Do what feels best to you and to the idea you have about the HTML structure in your head. If you are confused, come back to it and edit it. If you are sure, that **this** is the propper the classname - you're probably doing it right.


[Obecto]: http://obecto.com/page/team/
[BEM]: https://bem.info/method/
[SMACSS]: http://smacss.com
[Atomic Design]: http://patternlab.io/
[Grunt.js]: http://gruntjs.com
[Gulp]: http://gulpjs.com
[rule specificity]: http://www.smashingmagazine.com/2007/07/27/css-specificity-things-you-should-know/
[Signal.ly]: http://alpha.signal.ly
[autoprefixer]: https://www.npmjs.com/package/autoprefixer
[scss-lint]: https://github.com/brigade/scss-lint
[property sort order]: https://github.com/brigade/scss-lint/tree/master/data/property-sort-orders
[CSS Tricks's article]: https://css-tricks.com/pseudo-class-selectors/
[css guidelines]: http://cssguidelin.es
[here on csswizardry]: http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/
[at the cssguidelin.es]: http://cssguidelin.es/#bem-like-naming

*[CSS]: Cascadable Style Sheets
*[BEM]: Block Element Modifier
*[SMACSS]: Scalable Modular CSS
*[ToC]: Table of Contents
