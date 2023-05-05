Download Link: https://assignmentchef.com/product/solved-cse241-homework-4
<br>
Suppose that you are creating a fantasy role-playing game. In this game we have four different types of creatures: humans, cyberdemons, balrogs, and elves. To represent one of these creatures we might define a Creature class as follows:

Some of the members are given the others are left to you so that you can decide. Decide which of the members are going to be private or public.

<strong>class </strong>Creature {

<em>//a member data which defines the type</em>

<em>//a member data which stores the strength</em>

<em>//a member data which stores the hitpoints</em>

<em>//a helper function which returns the creature type</em>

Creature( );

<em>// Initialize to human, 10 strength, 10 hit points</em>

Creature(int newType, int newStrength, int newHit);

<em>// Initialize creature to new type, strength, hit points</em>

<em>// Also add appropriate accessor and mutator functions</em>

<em>// for type, strength, and hit points </em>int getDamage();

<em>// Returns amount of damage this creature</em>

<em>// inflicts in one round of combat</em>

};

Here is an implementation of the <sub>getSpecies( ) </sub>function:

string Creature::getSpecies()

{ <strong>switch </strong>(type)

{ <strong>case </strong>0: <strong>return </strong>“Human”; <strong>case </strong>1: <strong>return </strong>“Cyberdemon”; <strong>case </strong>2: <strong>return </strong>“Balrog”; <strong>case </strong>3: <strong>return </strong>“Elf”;

} <strong>return </strong>“Unknown”;

}

The getDamage( ) function outputs and returns the damage this creature can inflict in one round of combat. The rules for calculating the damage are as follows: • Every creature inflicts damage that is a random number r, where 0 &lt; r &lt;= strength. • Demons have a 5% chance of inflicting a demonic attack which is an additional 50 damage points. Balrogs and Cyberdemons are demons. • With a 10% chance elves inflict a magical attack that doubles the normal amount of damage. • Balrogs are very fast, so they get to attack twice.

A skeleton of <sub>getDamage( ) </sub>is given below:

int Creature::getDamage()

{ int damage;

<em>// All creatures inflict damage which is a // random number up to their strength </em>damage = (rand() % strength) + 1;

1

cout &lt;&lt; getSpecies() &lt;&lt; ” attacks for ” &lt;&lt; damage &lt;&lt; ” points!” &lt;&lt; endl;

<em>// Demons can inflict damage of 50 with a 5% chance </em><strong>if </strong>((type = 2) || (type == 1))

<em>// Elves inflict double magical damage with a 10% chance </em><strong>if </strong>(type == 3)

{

}

<em>// Balrogs are so fast they get to attack twice </em><strong>if </strong>(type == 2)

{

} <strong>return </strong>damage;

}

One problem with this implementation is that it is unwieldy to add new creatures. Rewrite the class to use inheritance, which will eliminate the need for the variable type. The Creature class should be the base class. The classes Demon, Elf, and Human should be derived from Creature. The classes Cyberdemon and Balrog should be derived from Demon. You will need to rewrite the getSpecies( ) and getDamage( ) functions so they are appropriate for each class. For example, the getDamage( ) function in each class should only compute the damage appropriate for that object. The total damage is then calculated by combining the results of getDamage( ) at each level of the inheritance hierarchy. As an example, invoking getDamage( ) for a Balrog object should invoke getDamage( ) for the Demon object which should invoke getDamage( ) for the Creature object. This will compute the basic damage that all creatures inflict, followed by the random 5% damage that demons inflict, followed by the double damage that balrogs inflict. Also include mutator and accessor functions for the private variables. Write a main function that contains a driver to test your classes. It should create an object for each type of creature and repeatedly outputs the results of getDamage( ).

<h1>Turn In</h1>

<ul>

 <li>A zip file containing all the <sub>.cpp </sub>and <sub>.h </sub>files of your implementation. Properly name your files according to the classes you your. Put your driver program(main function) in <sub>cpp</sub>.</li>

 <li>Create a simple <sub>MAKEFILE </sub>for your submission. (You can find tutorials for creating a simple make file. If you are having difficulty, send me an email.)</li>

 <li>Name of the file should be in this format: <sub>&lt;full_name&gt;_&lt;id&gt;.zip</sub>. Don’t send <sub>.rar </sub>or <sub>.7z </sub>or any other format. Properly create a <sub>.zip </sub>file from your source files.</li>

 <li>You don’t need to use an IDE for this assignment. Your code will be compiled and run in a command window.</li>

 <li>Your code will be compiled and tested on a Linux machine(Ubuntu). GCC will be used.</li>

 <li>Make sure you don’t get compile errors when you issue this command : <sub>g++ -std=c++11 &lt;any_of_your_files&gt;.cpp</sub>.</li>

 <li>Makes sure you don’t get link errors.</li>

</ul>