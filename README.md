Download Link: https://assignmentchef.com/product/solved-cmsc401-assignment-1-majority-element-finding
<br>
<h1></h1>

<ul>

 <li>Implement Majority-Element finding using Algorithm V from lecture slides</li>

 <li>Input:</li>

 <li>array of N positive integers – size of the problem is N n Output:</li>

 <li>1) <strong>majority element (M.E.) </strong>– element occurring more than N/2 times</li>

</ul>

(order of elements doesn’t matter), if M.E. exists n 2) <strong>-1, </strong>if the majority element does not exist in the array

<ul>

 <li>Input should be read into array of integers: int[] <u>(do not use</u></li>

</ul>

<u>ArrayList) </u>n The code should work on that array, without re-formatting the data e.g. into a linked list or any other data structure

<ul>

 <li>The algorithm should have <strong><u>O(N) time complexity </u></strong>n Use of any Java built-in functions/classes is NOT allowed n With the exception of functions from Scanner, System.in and</li>

</ul>

System.out (or equivalent) for input/output

<h1>Input-output formats</h1>

<table width="946">

 <tbody>

  <tr>

   <td width="38">••</td>

   <td width="618"><u>Input Format:</u>–     First line: a single integer number N&gt;=1, N&lt;=1,000,000–     Following N lines: each contains a single positive integer containing the elements of the array• Each integer will be &lt;=1,000,000,000–     Input will always be correct w.r.t. the specification above<u>Output format:</u>–     A single line, with a single integer:</td>

   <td width="166">Input 1:511001001100Output 1:100</td>

   <td width="123">Input 2:4100002100003Output 2:-1</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>-1 if the input array has no majority element</li>

 <li>X if integer X is the majority element of the input array</li>

</ul>

<h1>Algorithm V (from lecture)</h1>

<table width="464">

 <tbody>

  <tr>

   <td width="42">3</td>

   <td width="42">3</td>

   <td width="42">4</td>

   <td width="42">7</td>

   <td width="43">7</td>

   <td width="43">7</td>

   <td width="42">7</td>

   <td width="42">7</td>

   <td width="42">7</td>

   <td width="42">7</td>

   <td width="42">8</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>Observation: some pair of elements can be deleted from A without changing M.E. (if M.E. exists) – Example:</li>

 <li>Possible pairs and corresponding deletion effects:

  <ul>

   <li>(non-M.E., non-M.E.) -&gt; result doesn’t change</li>

   <li>(M.E., non-M.E.) -&gt; result doesn’t change – (M.E., M.E.)-&gt; result can change assuming M.E. exists</li>

  </ul></li>

 <li>Order in which pairs are deleted is not important</li>

 <li>But we don’t know which element is M.E.!</li>

</ul>

Algorithm V (from lecture)

<ul>

 <li>Solution:

  <ul>

   <li>Instead of Delete everything except (M.E., M.E.)</li>

   <li>Do Delete everything except (X,X)</li>

  </ul></li>

 <li>Move through the elements from left to right</li>

 <li>Keep deleting pairs of no-equal elements at every opportunity</li>

</ul>

<table width="464">

 <tbody>

  <tr>

   <td width="42">3</td>

   <td width="42">7</td>

   <td width="42">3</td>

   <td width="42">7</td>

   <td width="43">7</td>

   <td width="43">4</td>

   <td width="42">7</td>

   <td width="42">7</td>

   <td width="42">7</td>

   <td width="42">7</td>

   <td width="42">8</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>E. will be the only one remaining – Easy implementation with double-linked list • Example:

  <ul>

   <li>But we can also do these concepts for an array.</li>

  </ul></li>

</ul>

How?

<table width="464">

 <tbody>

  <tr>

   <td width="42">3</td>

   <td width="42">3</td>

   <td width="42">3</td>

   <td width="42">7</td>

   <td width="43">7</td>

   <td width="43">4</td>

   <td width="42">7</td>

   <td width="42">7</td>

   <td width="42">7</td>

   <td width="42">7</td>

   <td width="42">8</td>

  </tr>

 </tbody>

</table>

Algorithm V (from lecture)

<ul>

 <li>Array approach:

  <ul>

   <li>Assign a candidate-M.E. (c-ME) (init:1<sup>st </sup>element)</li>

   <li>As you sweep the array,</li>

  </ul></li>

 <li>do not delete c-ME, move forward</li>

 <li>delete a non-c-ME with one c-ME.</li>

 <li>If another element becomes most frequent in the array so far (i.e., a new c-ME), all instances of the previous one have already been deleted

  <ul>

   <li>One approach: keep current position and keep count of c-ME and decrease upon delete</li>

  </ul></li>

 <li>Location of c-MEs is not important, only their count</li>

</ul>

Algorithm V (from lecture)

<ul>

 <li>Boyer &amp; Moore approach

  <ul>

   <li>Select first element as candidate M.E., set counter to 1 – Move forward through the array. When we see:</li>

  </ul></li>

 <li>another copy of the c-ME -&gt; increase counter</li>

 <li>some other element -&gt; decrease counter</li>

 <li>If the counter becomes 0, assign a new c-ME at current</li>

</ul>

index

<ul>

 <li>previous c-ME lost the chance</li>

 <li>Once the entire array is traversed, c-ME will be the only</li>

</ul>

element left (if exists)

<h2>Input/output in Java</h2>

<ul>

 <li>Use Standard I/O to read input and write the result</li>

 <li>For Java, input: System.in, output: System.out</li>

 <li>“Do Not”s

  <ul>

   <li>Do not read from a disk file/write to disk file</li>

   <li>Do not write anything to screen except the result</li>

  </ul></li>

 <li>Ex: Human centric messages (“the result is”, “please enter..”)</li>

 <li>Automated grading via script will be used for checking correctness of your output</li>

</ul>