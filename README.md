# Based on Alpha_Beta pruning to solve the backgammon endgame(基于$\alpha-\beta$剪枝算法解快乐五子棋残局挑战)
### 1.简介
快乐五子棋是一种经典的策略游戏，玩家需要通过在棋盘上连线五个棋子获胜。然而，在复杂的残局中，寻找最佳走法可能非常困难。本项目通过构建博弈树并结合 **Alpha-Beta 剪枝算法**，能够在有限的计算资源下快速评估棋盘状态，找到最优或接近最优的解决方案。

该项目适用于：
- 棋类爱好者研究残局策略。
- AI 开发者学习博弈树搜索算法的实际应用。
- 教学用途，帮助理解 Alpha-Beta 剪枝的原理与实现。
### 2.项目文件
本项目目录下的文件夹及文件有:`Code`,`Result`,`Report.pdf`
> **Code文件夹:** 存储项目的核心python文件,example文件中存储快乐五子棋残局挑战的前20关对应的定义文件
> **Result文件夹:** 存储项目最后成功解决的实验结果,共通过了20关其中的16关
> **Report.pdf:** 为项目的完整实验报告,详细的介绍了项目的算法原理及代码优化过程,实验结果等;
### 3.算法原理

#### 博弈树搜索
博弈树是一种递归数据结构，用于模拟双方玩家的所有可能走法。每个节点代表一个棋盘状态，而边表示玩家的行动。通过递归遍历博弈树，可以找到当前状态下最优的走法。

#### Alpha-Beta 剪枝
Alpha-Beta 剪枝是一种优化技术，用于减少博弈树搜索中的冗余计算。其核心思想是：
- **Alpha**: 当前玩家能够获得的最大收益。
- **Beta**: 对手能够接受的最小损失。
- 在搜索过程中，如果某个分支的评估值已经不可能优于当前最优解，则直接剪枝，跳过该分支的进一步计算。

通过 Alpha-Beta 剪枝，我们可以在不牺牲结果质量的前提下，显著减少搜索时间。

#### 应用到五子棋
在快乐五子棋中，每一步都会改变棋盘的状态。我们使用以下步骤评估局面：
1. 构建博弈树，模拟双方所有可能的走法。
2. 使用评价函数评估棋盘状态（如连珠数量、潜在威胁等）。
3. 应用 Alpha-Beta 剪枝算法，快速找到最优解。
4. 通过不断调整各类棋型的评分来使策略达到最佳(对于进攻和防守的平衡)
   
### 4.安装配置
#### 环境要求
- Python版本：3.8+
- 依赖库：`numpy`, `pygame`等
  
### 5. 运行方法
在Code文件夹下运行命令:
- `python gobang.py --chess_file 残局文件名`
