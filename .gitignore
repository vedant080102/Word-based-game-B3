#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int x = 1, y = 1, Health = 10, run = 0;
char a[9][9], move='\0';
int sword=0;
char type[3][7]={{"Fire"},{"Water"},{"Plant"}};
char riddle[3][500]={{"Some try to hide, some try to cheat; but time will show, we always will meet. Try as you might to guess my name."},{" I’m alive, but without breath; I’m as cold in life as in death; I’m never thirsty, though I always drink."},{" What can run, but never walks; has a mouth, but never talks; has a head, but never weeps; has a bed, but never sleeps?"}};
char riddle_ans[3][10]={{"death"},{"fish"},{"river"}};

struct player_details
{
    char name[50];
}p1;

void intro();
void ground ();
void move_Player (char m);
void lantern ();
int input_check (char ideal1[], char ideal2[], char ideal3[]);
void monster (int mons_type);
void swordy (int sword_type);

void menu ();
void start ();
void help ();
void credits ();
void exit_game ();

char * _strtok_r (char *s, const char *delim, char **save_ptr)
{
  char *end;
  if (s == NULL)
    s = *save_ptr;
  if (*s == '\0')
    {
      *save_ptr = s;
      return NULL;
    }

  s += strspn (s, delim);
  if (*s == '\0')
    {
      *save_ptr = s;
      return NULL;
    }

  end = s + strcspn (s, delim);
  if (*end == '\0')
    {
      *save_ptr = end;
      return s;
    }
    *end = '\0';
  *save_ptr = end + 1;
  return s;
}

int main()
{
    Health = 10;
    x = 1;
    y = 1;

    /* Calling the function which will make our playground ready */
    //ground();

    intro();

    printf (" State your name, brave warrior:\t");
    gets (p1.name);

    intro();

    menu ();


    return 0;
}

void intro()
{
    system("cls");
    printf (" In a world of greed and animosity, the only thing that can save it is the Heart of the Fallen Titan\n\n Enter the Dungeon Hunt and free the world from its suffering by finding it!\n");
    printf ("\t\t\t\t\t Menu\n\t\t\t\ta. Start\tb. Help\n\t\t\t\tc. Credits\td. Exit\n\n");
}

void menu ()
{
    char ch;

    printf (" Enter your option from the Menu:\t");
    ch = getchar();

    intro();

    if (ch == 'a')
        start ();

    else if (ch == 'b')
        help ();

    else if (ch == 'c')
        credits();

    else if (ch == 'd')
        exit_game();

    else
    {
        //printf(" wrong input");
        menu();
    }

    /*
    switch (ch)
    {
    case 'a':
        start ();

    case 'b':
        help ();

    case 'c':
        credits ();

    case 'd':
        exit_game ();

    default:
        printf("wrong input");
    }
    menu ();
    */
}

void start ()
{
    printf (" So you chose to undertake the mission eh?\n Well %s, let me give you a lesson on how to survive in the dungeon\n\n The commands are:\n Movement:\t8 = forward\t4 = left\t6 = right\t2 = backward\t7 = lantern\t0 = End Game\n\n Also all actions other that this can be typed in by you\n\n In which direction would you like to move?\t", p1.name);
    scanf ("%c",&move);

    intro ();
    lantern ();

    ground ();

    // move is player input for movement
    while (move != '\0')
    {
        //move = zero is for exit
        printf (" Play next move—>\t");
        scanf ("%c",&move);

        intro ();

        if (move == '0')
            exit_game ();

        move_Player (move);

        lantern ();
    }

    exit_game();
}

void help ()
{
    printf (" Instructions\n The commands are:\n Movement:\t8 = forward\t4 = left\t6 = right\t2 = backward\t7 = lantern\t0 = End Game\n");

    system("pause");

    menu ();
}

void credits ()
{
    printf ("\t\t\t\tVedant\tVishnu\tShreyans\n\t\t\t\t1911117\t1911130\t1911124\n");

    system("pause");

    menu ();
}

void exit_game()
{
    printf ("You have fared well, my child. I hope to see you soon.\n");

    exit(0);
}

void ground ()
{
    /* Plotting the walls (w), demons (d), swords (s) and The Treasure (t) on our playground */
    int i, j;

    for (i=0;i<10;i++)
    {
        for (j=0;j<10;j++)
        {
            if (i==0 || i==9 || j==0 || j==9)
                a[i][j] = 'w';
        }
    }

    a[2][2]='w';
    a[2][3]='w';
    a[2][4]='w';
    a[2][6]='w';
    a[2][7]='w';
    a[3][2]='w';
    a[3][4]='w';
    a[3][6]='w';
    a[4][1]='w';
    a[4][2]='w';
    a[4][4]='w';
    a[4][6]='w';
    a[5][5]='w';
    a[5][6]='w';
    a[6][2]='w';
    a[6][3]='w';
    a[7][2]='w';
    a[7][4]='w';
    a[7][5]='w';
    a[7][6]='w';
    a[7][7]='w';
    a[7][8]='w';
    a[2][8]='f';
    a[3][3]='u';
    a[4][5]='s';
    a[6][1]='d';
    a[7][3]='v';
    a[8][5]='e';
    a[8][8]='t';
}

void move_Player (char m)
{
    //  This function checks the moves of the player
    int h = x, k = y;
    if (m == '2')
        /* Move forward*/
        x++;

    else if (m == '8' )
        /* Move backward */
        x--;

    else if (m == '6')
        /* Move towards right */
        y++;

    else if (m == '4')
        /* Move towards left */
        y--;

    else if (m== '7')
        //Lantern Function/
        lantern();

    else if (m == '0')
        exit_game();

    //else if (m == 'j')
    //        printf(" Wrong Input\n");

    if (a[x][y] == 'w')
    {
        /* If wall is found */
        printf(" Can't move here, there is a wall.\n");

        x = h;
        y = k;
    }

     /* If monster is found */
    else if (a[x][y] == 'd')
    {
        monster(1);

        if (run==1)
        {
            x=h;
            y=k;
            run=0;
        }
    }

    else if (a[x][y] == 'e')
    {
        monster(2);

        if (run==1)
        {
            x=h;
            y=k;
            run=0;
        }
    }

    else if (a[x][y] == 'f')
    {
        monster(3);

        if (run==1)
        {
            x=h;
            y=k;
            run=0;
        }
    }

    /* If sword is found */
    else if (a[x][y] == 's')
    {
        swordy(1);

        if (run==1)
        {
            x=h;
            y=k;
            run=0;
        }
    }

    else if (a[x][y] == 'u')
    {
        swordy(2);

        if (run==1)
        {
            x=h;
            y=k;
            run=0;
        }
    }

    else if (a[x][y] == 'v')
    {
        swordy(3);

        if (run==1)
        {
            x=h;
            y=k;
            run=0;
        }
    }

    else if (a[x][y] == 't')
    {
        /* If treasure is found */
        printf(" You have found treasure and won the game\n");
        move = 0;
    }
}

void lantern ()
{
    int i, j;

    ground();

    for (i = 0; i <= 9; i++)
    {
        printf ("\n ");
        for (j = 0; j <= 9; j++)
        {
            if (i == x && j == y)
                printf ("P ");

            else if (a[i][j] == 'w')
                printf ("* ");

            else if (a[i][j] == 'd'|| a[i][j] == 'e'|| a[i][j] == 'f')
                printf ("M ");

            else if (a[i][j] == 's'|| a[i][j] == 'u'|| a[i][j] == 'v')
                printf ("S ");

            else
                printf ("  ");
        }
    }
    printf("\n\n");
}

int input_check (char ideal1[], char ideal2[], char ideal3[])
{
	char c[3][50], b[50];
  	char *rest,*token;
  	char *pos;
	int count = 0, i, sum, flag1 = 0, flag2 = 0, flag3 = 0;

	getchar ();
	fgets (b,50,stdin);

    if ((pos=strchr(b, '\n')) != NULL)
        *pos = '\0';
	//scanf("%s",b);
	rest = b;

    while (strcmp(rest,"\0")!=0)
	{
		token = _strtok_r(rest," ",&rest);
		strcpy(c[count],token);
		count++;
	}

	for (i = 0; i < count; i++)

	{

		if (strcmp(c[i],ideal1) == 0)
			flag1 = 1;

		if (strcmp(c[i],ideal2) == 0)
			flag2 = 1;

		if (strcmp(c[i],ideal3) == 0)
			flag3 = -3;
	}

	sum = flag1 + flag2 + flag3;

	return sum;
}

void monster (int mons_type)
{
	int a, mons_adv, mons_def;

	printf ("A %s type monster appeared! What will you do? \n Will you risk it all and attack? Or run to save your life?\n (you can type in attack/kill to attack or run to run)\n", type[mons_type-1]);

	a = input_check ("attack","kill","run");

	if(a == 1)
	{
		mons_adv = mons_type+1;
		if (mons_adv == 4)
        {
            mons_adv = 1;
            mons_def = mons_type-1;
        }

		if (mons_def == 0)
            mons_def = 3;

		if (sword == mons_adv)
			printf ("You absolutely crushed your opponent. The monster didn't stand a chance!");

		if (sword == mons_type || sword == 0)
			printf ("You won the battle, but you lost half your HP \n");

		if (sword == mons_def)
		{
			printf ("You lost the battle. Start the game all over again.\n");
			x=1;
			y=1;
			sword=0;
		}
	}

	else if (a < 0)
	{
		printf ("You got away safely \n");
		run=1;
	}

	else
	{
		printf ("I'm sorry I didn't get that \n");
		monster(mons_type);
	}
}

void swordy (int sword_type)
{
    int a, b;

	printf (" Greetings, I am the Sphinx. To get the weapon laying behind me, you must first answer the following riddle:\n %s\n\n Please answer in just one word: ", riddle[sword_type-1] );
	//printf("hi");

	a = input_check(riddle_ans[sword_type-1],"z","x");

	//printf ("hi");

	if(a == 1)
	{
		printf ("\n You found a %s sword!!\n",type[sword_type-1]);
		sword = sword_type;
	}
	else
		printf ("\n That's wrong. You may try again by coming back here\n");
}
