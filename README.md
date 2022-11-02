# wardgame
#include<iostream>
#include<string>
#include<vector>
#include<algorithm>
#include<ctime>
#include<cctype>

using namespace std;

int main()
{
  const int MAX_WRONG=7;

  vector<string>words;
  words.push_back("mogura");
  words.push_back("oni");
  words.push_back("koria");
  srand(static_cast<unsigned int>(time(0)));
  random_shuffle(words.begin(),words.end());
  const string THE_WORD = words[0];
  int wrong=0;
  string soFar(THE_WORD.size(),'_');
  string used = "";

  cout << "ようこそ　文字あてゲームへ\n";

  while((wrong < MAX_WRONG) && (soFar !=THE_WORD))
    {
      cout << "\n\nあなたは間違えられる" << (MAX_WRONG - wrong);
      cout << "間違った回答\n";
      cout << "\n次のような文字が使われている\n" << used << endl;
      cout <<"\nいまのところ、その言葉は：\n" << soFar << endl;

      char guess;
      cout << "\n\n あなたの推測を入力してください:";
      cin >> guess;
      while (used.find(guess) != string::npos)
        {
  cout << "\nあなたはすでに入力してます" << guess << endl;
  cout << "あなたの推測を入力してください";
  cin >> guess;
          }

  used +=guess;

   if(THE_WORD.find(guess) != string::npos)
   {
     cout << "いいね！" << guess << "それがワードです。\n";

     for (int i=0; i < THE_WORD.length(); ++i)
       {
         if(THE_WORD[i] == guess)
         {
           soFar[i] = guess;
         }
       }

       
   }
      else
   {
     cout << "すみません" << guess << "そのワードは違います\n";
     ++wrong;
     }
   }

if (wrong==MAX_WRONG)
{
  cout << "\nあなたの負けです";
  
}
  else
{
  cout << "\nあなたの勝ちです";
  
}
  cout << "\n今回のお題は" << THE_WORD << endl;

return 0;

  
  




}
![MicrosoftTeams-image (9)](https://user-images.githubusercontent.com/104427299/199404165-593b1193-ed12-4f1f-b595-ab1d3f6e1253.png)
